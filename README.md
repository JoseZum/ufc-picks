# UFC Picks – Distributed Prediction Platform
A full-stack system where users predict UFC fight outcomes and compete in real-time leaderboards. Designed with scalable architecture, automated data ingestion, and CI/CD-driven reliability.

## Live System
**Frontend:** https://ufc-picks-frontend.vercel.app<br>**Backend API:** Render Deployment<br>
**Database:** MongoDB Atlas<br>
**Storage/CDN:** AWS S3 + CloudFront<br>

##  Repositories

| Service | Repository |
|--------|------------|
|  Frontend | https://github.com/JoseZum/ufc-picks-frontend |
|  Backend | https://github.com/JoseZum/ufc-picks-backend |
|  Scraper | https://github.com/JoseZum/ufc-picks-scraper 

## Architecture Diagram

### Image Resolution Strategy

The system supports two image resolution modes.

S3 is the primary image storage when available. Images scraped from Tapology are uploaded to S3 and served publicly through CloudFront.

MongoDB stores image keys and source references, allowing the system to degrade gracefully if S3 is unavailable or storage limits are reached. In cache mode, the backend operates without writing to S3 and resolves images via proxying or cached references.

This design ensures that the application remains functional even if the primary object storage is temporarily unavailable.
