🧶 Textile Platform
<p align="center">
<img src="[URL_TO_TEXTILE_LOGO.svg]" alt="Textile Logo" width="180"/>
</p>
Engineered to scale, built for performance. The proprietary social media platform successor.
🔒 Confidentiality Notice
This software is Proprietary and intended solely for internal organizational use. All source code, architectural designs, and associated documentation are confidential and must not be disseminated externally.
🗺️ Architecture Overview
Textile employs a Hybrid Polyglot Microservices Architecture to deliver high performance and exceptional scalability, with a clear separation of concerns between performance-critical and business-logic services.
| Component | Technology Stack | Purpose |
|---|---|---|
| Performance Critical | Rust (Async, Tokio) | API Gateway, Media Processing, Real-Time WebSockets, High-Speed Caching. |
| Business Logic | Kotlin (JVM) | CRUD Services (Post, User), Timeline, Messaging, Moderation, Analytics, Ads. |
| Data Stores | PostgreSQL, Cassandra, Redis, Elasticsearch | Relational Data, High-Volume Time Series (DMs), Caching, Semantic Search. |
| Infrastructure | Kubernetes, Istio, Terraform, Helm | Orchestration, Service Mesh, Infrastructure as Code (IaC). |
| Event Bus | Apache Kafka | Asynchronous communication, notifications, and analytics ingestion. |
| Clients | iOS (Swift/SwiftUI), Android (Kotlin/Compose) | Native, high-fidelity user experiences. |
> Gating Strategy (Key Feature): All feature visibility (e.g., showing 'Follow' vs. 'Edit Profile') is driven by a backend-computed viewer_context returned by the user-service. The native clients utilize reusable ActionGater components to ensure consistent, secure, and error-proof UI rendering.
> 
For an in-depth system design, refer to docs/architecture/system-design.md.
✨ Core Feature Set
The platform includes a comprehensive set of features to rival large-scale social networks:
📱 User Interaction
 * User Management: Profiles, following, blocking, verification, and GDPR/CCPA-compliant privacy controls.
 * Content & Engagement: CRUD operations for posts, replies, and quotes, plus likes, reposts, and bookmarks.
 * Real-Time Feeds: Algorithmic, personalized Timelines powered by ML ranking and integrated advertising.
 * Direct Messaging (DM): Real-time chat with typing indicators, attachments, and End-to-End Encryption.
 * Groups & Communities: Dedicated service for group creation, membership, and topic discovery.
🧠 Intelligence & Performance
 * Recommendations: ML services employing Collaborative Filtering, Content-Based methods, and Trending analysis.
 * Search & Discovery: Full-text indexing via Elasticsearch, enhanced with Vector Embeddings for semantic search.
 * Media Processing: GPU-accelerated video transcoding, image compression, and thumbnail generation using dedicated Rust services.
 * Fault Tolerance: Circuit breakers and retry logic implemented across gRPC calls via Istio and shared middleware.
🛡️ Security & Operations
 * Auth & Authz: JWT, OAuth2, and MFA support. Clear separation of Authentication (in Gateway) and Authorization (in auth-service).
 * Moderation: Automated toxicity and spam detection, bot classification, user reporting, and appeals management.
 * Analytics: Real-time event consumption via Kafka for metrics aggregation and impressions tracking.
 * Monetization: Dedicated services for Ads (Targeting & Auction) and Premium Subscriptions (Stripe/PayPal integration).
💻 Getting Started (Local Development)
Prerequisites
You will need the following tools installed and configured:
 * Docker and Docker Compose
 * Kubernetes (Local clusters like Minikube/K3s are helpful)
 * Terraform and Helm
 * Rust Toolchain (Stable)
 * JDK 17+ and Gradle (for Kotlin services)
 * Xcode (for iOS development) / Android Studio (for Android development)
🚀 Setup and Execution
 * Clone the Repository:
   git clone <internal-repository-url>
cd Textile/backend

 * Initialize and Launch Backend:
   # Set up databases, configurations, and shared libraries
./scripts/setup.sh

# Start all microservices in the background
docker-compose up -d

# Optional: Populate initial data for testing
./scripts/seed-data.sh

 * Client Setup:
| Client | Directory | Setup Instruction |
|---|---|---|
| iOS | ../ios/ | Open Textile.xcodeproj in Xcode and run pod install. |
| Android | ../android/ | Import android/ into Android Studio and Sync Gradle. |
✅ Testing
Testing is multi-layered, ensuring reliability from unit level up to cross-service dependencies.
| Type | Location | Command/Tool | Purpose |
|---|---|---|---|
| Unit | Service directories | ./scripts/test-all.sh | Validate individual component logic. |
| Integration | backend/tests/integration/ | ./scripts/integration-tests.sh | Cross-service testing using Testcontainers (e.g., timeline-ads.kt). |
| Client | Xcode / Android Studio | Built-in test runners | Validate UI functionality and gating logic. |
📄 Documentation
 * Architecture & Design: docs/architecture/
 * API Specification: docs/api/openapi.yaml
 * Runbooks & Operations: docs/runbooks/ (Deployment, Monitoring, Scaling procedures)
🤝 Contribution Guidelines
Contributions are strictly limited to internal team members.
 * Branch off of the main branch.
 * Follow the architectural and coding standards.
 * Submit Pull Requests (PRs) for review and approval by an assigned owner.
Last Updated: November 17, 2025
