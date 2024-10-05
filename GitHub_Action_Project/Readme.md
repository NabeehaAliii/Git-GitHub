# **Resume Hosting Using GitHub Actions and AWS**

### **Project Description**
This project demonstrates how to use **GitHub Actions** to automate the deployment of a static resume website hosted on **AWS S3** and delivered using **AWS CloudFront**. Every code push will trigger an automatic deployment, ensuring continuous integration and delivery for the website.

### **Technologies Used**
- **GitHub Actions** for CI/CD
- **AWS S3** for static website hosting
- **AWS CloudFront** for content delivery
- **Route 53** for domain management
- **AWS IAM** for user and permission management
- **HTML/CSS/JavaScript** for the resume website

---

### **Steps Breakdown**

#### **1. Create AWS IAM User for GitHub Actions**
To securely access AWS services from GitHub Actions, create a new IAM user.
- **Go to AWS Console > IAM > Create User** with programmatic access.
- Attach permissions to use S3, CloudFront, and Route 53.
- **Store AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY** securely (they will be used as GitHub Secrets).
  
<img width="960" alt="create-new-user" src="https://github.com/user-attachments/assets/b8812a52-4929-4374-b9f9-f8ee0295e43f">

#### **2. Configure S3 Bucket and CloudFront**
- Create an S3 bucket for hosting the static website.
- Enable static website hosting for the S3 bucket.
- Create a CloudFront distribution to serve the static website using the S3 bucket as the origin.

<img width="960" alt="MadeCloudFrontDist_AND_AllowCNAMEAlternative" src="https://github.com/user-attachments/assets/14a18ac9-ae50-4f3b-ba36-19a44d04a383">


#### **3. Configure Route 53 Domain**
- If using a custom domain, configure **Route 53** to point the domain to the CloudFront distribution.
- Create an A record (Alias) pointing to the CloudFront domain.
  
<img width="960" alt="MadeRout53Alias" src="https://github.com/user-attachments/assets/71b6fe55-8f1a-4054-9c72-04c8f90e4ee3">


#### **4. Set Up GitHub Secrets**
- Navigate to your GitHub repository's settings.
- Add your **AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY**, **CLOUDFRONT_DISTRIBUTION_ID** as repository secrets to allow GitHub Actions to access AWS services.

<img width="960" alt="MadeCredentialsinSecret" src="https://github.com/user-attachments/assets/d28251e3-3314-4d7b-b2e8-76ee5c58941e">

#### **5. Write GitHub Actions Workflow**
Create a workflow file (.yml) under `.github/workflows` in your GitHub repository. This file will define the steps for deploying the website to S3 and invalidating the CloudFront cache whenever a push occurs to the `main` branch.

Example of a GitHub Actions workflow:
```yaml
name: Portfolio Deployment

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v1

    - name: Configure AWS Credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: ${{ secrets.AWS_REGION }}

    - name: Deploy to S3 bucket
      run: |
        aws s3 sync ./ s3://github-action-resume-hosting.click --delete

    - name: Invalidate CloudFront Cache
      run: |
        aws cloudfront create-invalidation --distribution-id ${{ secrets.CLOUDFRONT_DISTRIBUTION_ID }} --paths "/*"
```

#### **6. Push Code to GitHub**
- **Initialize** the Git repository locally.
  ```bash
  git init
  git remote add origin https://github.com/username/your-repo.git
  ```
- **Add and Commit** your code.
  ```bash
  git add .
  git commit -m "Initial commit"
  ```
- **Push** the code to the remote repository.
  ```bash
  git push origin main
  ```
 <img width="960" alt="Make-Repository_and_push_code" src="https://github.com/user-attachments/assets/e902b2cb-2631-431c-9fa4-292a84e7cad9">


#### **7. Automate Deployment Using GitHub Actions**

- Once code is pushed, the GitHub Actions workflow will trigger automatically.
- It will upload the website files to the S3 bucket and invalidate the CloudFront cache to serve the latest version of the website.
  
<img width="960" alt="pushActivatesDeployment" src="https://github.com/user-attachments/assets/1c0a50f7-f450-4395-8a4f-34c757caa167">



#### **8. Verify the Website**
After deployment, visit the domain to verify that the website is live.
  
<img width="960" alt="Successfully_hosted_resume" src="https://github.com/user-attachments/assets/6956a883-c5a3-46d0-8bd8-1e4002884cc5">

---

### **Learning Outcomes**
- Automated deployments using GitHub Actions.
- Experience in using AWS services such as **S3**, **CloudFront**, and **Route 53**.
- Gained understanding of using IAM users and GitHub Secrets for secure access to AWS.
- Developed a hands-on CI/CD pipeline to continuously deliver changes to a live website.

---

### **Important Notes**
- Ensure your AWS permissions are configured correctly for S3, CloudFront, and Route 53.
- Remember to configure your **GitHub Secrets** securely to avoid exposing your credentials.
- Keep your CloudFront distribution invalidations limited to avoid incurring extra costs.

---

### **Repository Link**
For full implementation and code, refer to the GitHub repository:
[GitHub Resume Hosting Repository](https://github.com/NabeehaAliii/GitHubAction_Project)

---
