# DALVacationHome - Serverless Cloud Architecture

## **Overview**
This document outlines the architecture and deployment of the **DALVacationHome** application, designed to provide room booking and management using serverless cloud services. The project leverages **AWS and GCP** for a fully scalable, event-driven cloud solution, integrating **data analytics, notifications, and automation** while adhering to **best security and performance practices**.

## **Project Scope**
- **User Registration & Booking System**: Allows users to register, login, and book vacation homes.
- **Cloud-Native & Serverless**: Utilizes AWS Lambda, GCP Cloud Functions, and event-driven messaging services.
- **Infrastructure as Code (IaC)**: Uses CloudFormation and Terraform for automated deployment.
- **Security & Monitoring**: Implements IAM best practices, encrypted storage, and real-time monitoring.

## **Architecture Components**
The **DALVacationHome** project is divided into multiple cloud-driven components:

### **1. Data Analytics & Visualization**
The **Looker Studio Architecture** enables real-time admin dashboards for login statistics and user details.

#### **Components Used:**
- **Looker Studio**: Frontend visualization of user login statistics and details.
- **BigQuery (GCP)**: Stores user activity logs in `user_data` dataset.
- **Cloud Functions (GCP)**:
  - `SaveUserDetails Function`: Updates the `user_details` table.
  - `SaveLoginInfo Function`: Stores login activity in `login_info` table.
- **Admin Dashboard**: Fetches insights for user behavior and system analytics.

### **2. Notifications & Event Handling**
The **Notifications Architecture** manages event-driven notifications for user actions and booking requests.

#### **Components Used:**
- **API Gateway**: Handles requests for user login, registration, and booking.
- **AWS Lambda Functions**:
  - `Login/Register Notification Lambda`: Sends notifications on user events.
  - `BookingRequestPublisher Lambda`: Publishes booking events to a queue.
  - `BookingApproval Notification Lambda`: Processes approval notifications.
- **Amazon SNS & SQS**:
  - **Notification Topic**: Sends email notifications for successful registrations.
  - **Booking Queue**: Processes booking approvals asynchronously.
- **Email Notifications**: Sent to users upon successful registration, login, or booking status updates.

## **Deployment & Automation**
- **Infrastructure as Code (IaC)**:
  - AWS CloudFormation and Terraform automate the provisioning of cloud resources.
- **Auto Scaling & Serverless**:
  - Lambda functions handle event-driven tasks without persistent infrastructure.
  - Cloud Functions (GCP) ensure seamless data processing.
- **Monitoring & Security**:
  - AWS CloudWatch and GCP Stackdriver track system health and logging.
  - IAM roles enforce **least privilege access** to all cloud services.

## **Security Measures**
- **IAM Role-Based Access Control**: Ensures least privilege access.
- **VPC & Private Subnets**: Isolates backend resources for security.
- **Secrets Manager**: Securely stores credentials and API keys.
- **HTTPS Encryption**: API Gateway enforces secure communication.

## **Scalability & Cost Optimization**
- **Auto Scaling**: Adjusts resources dynamically based on workload.
- **BigQuery Optimization**: Uses partitioning for efficient analytics processing.
- **Serverless Execution**: Minimizes compute costs by eliminating idle resources.
- **S3 Lifecycle Policies**: Stores infrequently accessed data in cost-efficient storage classes.

## **Future Enhancements**
- **AI-Based Booking Recommendations**: Use ML models to suggest vacation homes.
- **Chatbot Integration**: Implement AWS Lex for user interactions.
- **Multi-Region Deployment**: Expand across AWS and GCP regions for resilience.
- **Advanced Caching**: Integrate Redis (Amazon ElastiCache) for performance improvement.

## **Diagrams**
### **Looker Studio Architecture**
<img width="499" alt="LookerStudioArchitecture" src="https://github.com/user-attachments/assets/f5a211b9-086a-4c52-90b8-1338584ae93e" />


### **Notifications Architecture**
<img width="534" alt="NotificationsArchitecture" src="https://github.com/user-attachments/assets/a7060b8d-afa5-4a39-8eac-f5e2cdcb9622" />

### **System Architecture**
![image](https://github.com/user-attachments/assets/83198804-26bc-45fd-9537-1a7836035fd1)


