---
name: n8n-business-automation
description: Build and test n8n workflows for business process automation. Use when creating automation workflows with core nodes (webhook, HTTP, set, function, if), connecting data flows, testing workflows, or deploying business automation processes.
---

# n8n Business Process Automation

Build and test automation workflows using core nodes and connections.

## When to Apply

- Creating business process automation workflows
- Setting up data flows between webhook triggers and HTTP requests
- Building conditional logic with If/Switch nodes
- Testing workflows before production deployment

## Critical Rules

**Webhook Testing vs Production**: Use Test URL during development, Production URL when active

```json
// Development phase - use Test URL
"Listen for Test Event" button -> displays data in workflow

// Production phase - use Production URL
Active workflow -> no data display, check Executions tab
```

**Connection Structure**: Always define both source and target in connections

```json
// WRONG - incomplete connection
"connections": {
  "Webhook": {}
}

// RIGHT - complete connection definition
"connections": {
  "Webhook": {
    "main": [
      [{"node": "HTTP Request", "type": "main", "index": 0}]
    ]
  }
}
```

## Key Patterns

### Basic Automation Workflow

```json
{
  "nodes": [
    {
      "name": "Webhook",
      "type": "n8n-nodes-base.webhook",
      "parameters": {
        "httpMethod": "POST",
        "path": "process-order",
        "responseMode": "lastNode"
      }
    },
    {
      "name": "If",
      "type": "n8n-nodes-base.if",
      "parameters": {
        "conditions": {
          "conditions": [{
            "leftValue": "={{ $json.status }}",
            "rightValue": "pending",
            "operator": {"type": "string", "operation": "equals"}
          }]
        }
      }
    },
    {
      "name": "HTTP Request",
      "type": "n8n-nodes-base.httpRequest",
      "parameters": {
        "method": "POST",
        "url": "https://api.example.com/process",
        "sendBody": true,
        "bodyParameters": {
          "parameters": [
            {"name": "id", "value": "={{ $json.id }}"},
            {"name": "status", "value": "processed"}
          ]
        }
      }
    }
  ],
  "connections": {
    "Webhook": {"main": [[{"node": "If", "type": "main", "index": 0}]]},
    "If": {"main": [[{"node": "HTTP Request", "type": "main", "index": 0}], []]}
  }
}
```

### Schedule-Based Automation

```json
{
  "name": "Schedule Trigger",
  "type": "n8n-nodes-base.scheduleTrigger",
  "parameters": {
    "rule": {
      "interval": [{
        "field": "days",
        "daysInterval": 1,
        "triggerAtHour": 9,
        "triggerAtMinute": 0
      }]
    }
  }
}
```

### Data Transformation with Set Node

```json
{
  "name": "Set",
  "type": "n8n-nodes-base.set",
  "parameters": {
    "keepOnlySet": true,
    "values": {
      "string": [
        {"name": "processedBy", "value": "={{ $json.employeeName }}"},
        {"name": "status", "value": "completed"}
      ],
      "number": [
        {"name": "orderId", "value": "={{ $json.orderID }}"}
      ]
    }
  }
}
```

### Multiple Conditions with AND Logic

```json
{
  "conditions": {
    "conditions": [
      {
        "leftValue": "={{ $json.age }}",
        "rightValue": "18",
        "operator": {"type": "number", "operation": "gte"}
      },
      {
        "leftValue": "={{ $json.country }}",
        "rightValue": "US",
        "operator": {"type": "string", "operation": "equals"}
      }
    ],
    "combinator": "and"
  }
}
```

## Testing Workflows

**Manual Testing**: Use Manual Trigger + Execute Workflow button
```json
{
  "name": "Manual Trigger",
  "type": "n8n-nodes-base.manualTrigger",
  "position": [250, 300]
}
```

**Production Deployment**: Set workflow to Active via API
```bash
curl -X PATCH https://your-instance/api/v1/workflows/123 \
  -H "X-N8N-API-KEY: your-key" \
  -d '{"active": true}'
```

**Monitor Executions**: Check execution status
```bash
curl -X GET https://your-instance/api/v1/executions?status=error&limit=10 \
  -H "X-N8N-API-KEY: your-key"
```

## Common Mistakes

- **Missing webhook path**: Always specify custom path in production - `"path": "my-endpoint"`
- **Incomplete connections**: Define both source node and target with proper indexes
- **Wrong expression syntax**: Use `{{ $json.field }}` not `$json.field`
- **Testing with active workflow**: Keep workflow inactive during development, use Test URLs
