# Logic Log – GitHub API Rate Limit Handling

GitHub API enforces rate limits:
- 60 requests/hour (unauthenticated)
- 5000 requests/hour (authenticated)

## My Approach:

1. **Authentication**
   - Used GitHub Personal Access Token
   - Increased limit to 5000 requests/hour

2. **Batch Processing**
   - Used Split In Batches node
   - Processed limited users per cycle

3. **Delay Mechanism**
   - Added Wait node (1–2 seconds delay)
   - Prevents hitting burst limits

4. **Monitoring Headers**
   - Checked:
     - X-RateLimit-Remaining
     - X-RateLimit-Reset

5. **Fail-Safe**
   - Workflow pauses when limit is low
   - Resumes after reset time