# Logging Standards

## Required Context Fields

Include these identifiers in logs whenever available:

| Field | Description | Example |
|-------|-------------|---------|
| `sessionId` | Session identifier | `sess_abc123` |
| `userId` | User identifier | `U12345` |
| `requestId` | Request/correlation ID | `req_xyz789` |
| `traceId` | Distributed trace ID | `trace_...` |

Adapt field names to your domain (e.g., `slackUserId`, `botId`, `threadKey`).

## Log Levels

| Level | Use For |
|-------|---------|
| `debug` | Development info, verbose details |
| `info` | Normal operations, state changes |
| `warn` | Recoverable issues, degraded state |
| `error` | Failures requiring attention |

## Best Practices

### Variable Scoping

Declare tracking variables outside try blocks so they're available in catch:

```typescript
let sessionId: string | undefined;
try {
  sessionId = await getSession();
  // ...
} catch (error) {
  logger.error('Operation failed', error, { sessionId }); // Available!
}
```

### Context Building

Use `logger.withContext()` to build up context through request lifecycle:

```typescript
const log = logger.withContext({ sessionId, userId });
log.info('Processing request');
// ... later ...
log.info('Request complete', { duration });
```

### Error Logging

Always log errors with full context:

```typescript
logger.error('Queue processing failed', error, {
  sessionId,
  attempt,
  messageId,
});
```

### Retry Visibility

Include `attempt` count in queue/retry processing:

```typescript
logger.info('Processing message', { messageId, attempt: 2 });
```

### Helper Functions

Pass context to helpers that do their own logging:

```typescript
async function processItem(item: Item, ctx: LogContext) {
  const log = logger.withContext(ctx);
  log.debug('Processing item', { itemId: item.id });
}
```
