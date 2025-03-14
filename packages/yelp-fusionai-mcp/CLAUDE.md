# CLAUDE.md - Yelp Fusion MCP Server Guidelines

## Build/Test/Lint Commands
- Build: `npm run build`
- Start: `npm start`
- Dev mode: `npm run dev`
- Run tests: `npm test`
- Run single test: `npm test -- -t "test name"`
- Lint: `npm run lint`
- Format: `npm run format`

## Code Style Guidelines
- TypeScript with strict type checking
- Use async/await for asynchronous operations
- Use camelCase for variables and functions
- Use PascalCase for classes and interfaces
- Handle all errors with try/catch blocks
- Format responses as Markdown for better readability
- Prefer named exports over default exports
- Keep functions small and focused on a single task
- Document function parameters with JSDoc comments
- Use the Zod library for validation and schema definition
- Follow MCP specifications for all protocol interactions

## Project Structure
- `/src/services/api/` - API clients organized by category
- `/src/services/yelp.ts` - Main service that aggregates all API clients
- `/src/index.ts` - MCP server implementation with tool definitions

## Available Tools
- yelpQuery - Natural language business search
- yelpBusinessSearch - Parameter-based business search
- yelpBusinessDetails - Get business details by ID
- yelpBusinessReviews - Get business reviews
- yelpReviewHighlights - Get highlighted snippets from reviews
- yelpEventsSearch - Search for events in a location
- yelpEventDetails - Get detailed information about a specific event
- yelpFeaturedEvent - Get the featured event for a location

### Events Tools
- yelpEventsSearch - Search for events in a location
- yelpEventDetails - Get detailed information about a specific event
- yelpFeaturedEvent - Get the featured event for a location

### Categories Tools
- yelpGetCategories - Get all business categories from Yelp
- yelpGetCategoryDetails - Get detailed information about a specific category
- yelpSearchCategories - Search for business categories by name

### Advertising Tools
- yelpCreateAdProgram - Create a new advertising program
- yelpListAdPrograms - List all advertising programs
- yelpGetAdProgram - Get details of a specific advertising program
- yelpModifyAdProgram - Modify an existing advertising program
- yelpAdProgramStatus - Get status information for an advertising program
- yelpPauseAdProgram - Pause an active advertising program
- yelpResumeAdProgram - Resume a paused advertising program
- yelpTerminateAdProgram - Terminate an advertising program

### OAuth Tools
- yelpGetOAuthToken - Get an OAuth access token (v2 or v3)
- yelpRefreshOAuthToken - Refresh an OAuth v3 access token
- yelpRevokeOAuthToken - Revoke an OAuth access token
- yelpGetOAuthTokenInfo - Get information about an OAuth token

### Waitlist Tools
- yelpWaitlistPartnerRestaurants - Get restaurants that support Yelp Waitlist
- yelpWaitlistStatus - Get current waitlist status for a business
- yelpWaitlistInfo - Get detailed waitlist configuration for a business
- yelpJoinWaitlist - Join a restaurant's waitlist remotely
- yelpOnMyWay - Notify a restaurant that you're on your way
- yelpCancelWaitlistVisit - Cancel a waitlist visit
- yelpWaitlistVisitDetails - Get details about a waitlist visit

### Business Subscriptions Tools
- yelpGetSubscriptionPlans - Get available subscription plans
- yelpGetActiveSubscription - Get active subscription for a business
- yelpCreateSubscription - Create a new subscription
- yelpUpdateSubscription - Update an existing subscription
- yelpCancelSubscription - Cancel a subscription
- yelpGetSubscriptionUsage - Get subscription usage data
- yelpGetSubscriptionHistory - Get subscription history

### Checkout Tools
- yelpGetPaymentMethods - Get a list of payment methods
- yelpGetPaymentMethod - Get details for a specific payment method
- yelpCreatePaymentMethod - Create a new payment method
- yelpDeletePaymentMethod - Delete a payment method
- yelpGetInvoices - Get a list of invoices
- yelpGetInvoice - Get details for a specific invoice
- yelpPayInvoice - Pay an invoice using a payment method
- yelpGetPayments - Get a list of payments
- yelpGetPayment - Get details for a specific payment
- yelpRefundPayment - Request a refund for a payment

### Claim Business Tools
- yelpCheckClaimEligibility - Check if a business is eligible for claiming
- yelpSubmitBusinessClaim - Submit a claim for a business
- yelpGetClaimStatus - Get the status of a business claim
- yelpVerifyClaimCode - Submit verification code for a claim
- yelpCancelClaim - Cancel a pending business claim

### User Management Tools
- yelpGetUserProfile - Get the current user's profile
- yelpGetUserById - Get a user profile by ID
- yelpUpdateUserProfile - Update the current user's profile
- yelpGetUserPreferences - Get the current user's preferences
- yelpUpdateUserPreferences - Update the current user's preferences
- yelpGetFriends - Get a user's friends
- yelpGetUserCollections - Get a user's collections
- yelpGetCollectionDetails - Get details for a specific collection
- yelpCreateCollection - Create a new collection
- yelpUpdateCollection - Update an existing collection
- yelpDeleteCollection - Delete a collection
- yelpGetCollectionItems - Get items in a collection
- yelpAddBusinessToCollection - Add a business to a collection
- yelpRemoveBusinessFromCollection - Remove a business from a collection

### Data Ingestion Tools
- yelpListDataSources - List all data sources
- yelpGetDataSource - Get details about a specific data source
- yelpCreateDataSource - Create a new data source
- yelpUpdateDataSource - Update an existing data source
- yelpDeleteDataSource - Delete a data source
- yelpListDataIngestionJobs - List all data ingestion jobs
- yelpGetDataIngestionJob - Get details about a specific data ingestion job
- yelpCreateDataIngestionJob - Create a new data ingestion job
- yelpUpdateDataIngestionJob - Update an existing data ingestion job
- yelpCancelDataIngestionJob - Cancel a data ingestion job
- yelpRetryDataIngestionJob - Retry a failed data ingestion job

### Leads Management Tools
- yelpGetLeads - Get list of leads with optional filtering
- yelpGetLead - Get details about a specific lead
- yelpCreateLead - Create a new lead
- yelpUpdateLead - Update an existing lead
- yelpDeleteLead - Delete a lead
- yelpGetLeadNotes - Get notes for a lead
- yelpAddLeadNote - Add a note to a lead
- yelpDeleteLeadNote - Delete a note from a lead
- yelpGetLeadActivities - Get activity history for a lead
- yelpAddLeadActivity - Add an activity to a lead
- yelpBulkUpdateLeads - Update multiple leads in bulk
- yelpBulkDeleteLeads - Delete multiple leads in bulk
- yelpImportLeads - Import leads from a data source
- yelpExportLeads - Export leads to a file
- yelpGetExportStatus - Check status of an export job
- yelpGetLeadStatistics - Get statistics about leads

### Respond Reviews Tools
- yelpRespondReviewsGetToken - Get an OAuth access token for responding to reviews
- yelpRespondReviewsBusinesses - Get businesses that the user can respond to reviews for
- yelpRespondReviewsBusinessOwner - Get business owner information
- yelpRespondToReview - Respond to a review as a business owner

## Request/Response Patterns
Each tool follows a similar pattern:
1. Validate user input with Zod
2. Call the appropriate Yelp API endpoint
3. Transform the response into formatted Markdown
4. Return the formatted content to the user