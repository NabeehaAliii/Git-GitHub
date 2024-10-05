# **Overview: Resume Hosting with GitHub Actions and AWS**

### **Project Purpose**
The goal of this project is to demonstrate how to automate the deployment of a static resume website using **GitHub Actions** with **AWS S3** and **AWS CloudFront**. By setting up a CI/CD pipeline, we can ensure that each time new code is pushed to the repository, the website is automatically updated and delivered via AWS services.

### **Key Technologies**
- **GitHub Actions**: Automation tool for running workflows on code changes.
- **AWS S3**: Used for hosting the static resume website.
- **AWS CloudFront**: Content delivery network (CDN) to serve the website with low latency.
- **AWS IAM**: To manage secure access to AWS services.
- **Route 53**: For domain management and routing.
  
### **What We Achieve**
- **Continuous Deployment**: With GitHub Actions, any push to the `main` branch triggers the automatic deployment of the website to S3.
- **Content Delivery**: CloudFront speeds up website delivery globally, ensuring fast performance for users.
- **Custom Error Handling**: Set up custom error pages (like 404 or 403 errors) using CloudFront for a better user experience.
- **Domain Management**: If you own a custom domain, Route 53 can help connect it to your website hosted on AWS.

### **High-Level Workflow**
1. **Create AWS IAM User**: For secure access to S3 and CloudFront.
2. **Host Static Website on S3**: Upload your resume files to S3.
3. **Configure CloudFront**: Use CloudFront for better performance and global delivery.
4. **Automate with GitHub Actions**: Each code push updates the S3-hosted site and clears CloudFront cache.

### **Final Outcome**
By following this project, you will have a fully automated system that hosts your resume on AWS, ensuring that changes you make in your GitHub repository are immediately reflected on your live site.

---
