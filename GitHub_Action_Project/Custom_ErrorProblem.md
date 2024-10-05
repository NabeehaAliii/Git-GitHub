# **CloudFront Custom Error Handling Setup**

## **Problem Statement**

While hosting a static website on **Amazon S3** with **CloudFront** as the CDN, certain issues were encountered:
- **403 Access Denied Errors**: When users attempted to access restricted pages or files, CloudFront returned the default XML error response, which provided a poor user experience.
- **404 Not Found Errors**: Similarly, accessing non-existent URLs resulted in an unstyled XML error message rather than a custom, user-friendly error page.

### **Requirements**:
- Configure CloudFront to serve a custom error page (`error404.html`) for both **403 (Access Denied)** and **404 (Not Found)** errors.
- Ensure that the error page returns a **200 HTTP response code** for a consistent user experience.

## **Solution**

### 1. **Create a Custom Error Page (`error404.html`)**
   - A simple `error404.html` page was created to inform users that the requested page could not be found or access is restricted.
   - The page includes a friendly error message and a link to navigate back to the homepage.

### 2. **Configure CloudFront to Serve the Custom Error Page**
   - Accessed the **CloudFront** distribution settings.
   - Under the **Error Pages** tab, created custom error responses for both **403** and **404** errors:
     - **403 (Access Denied)**:
       - Set the error response to serve `/error404.html` when a **403** error occurs.
       - Configured CloudFront to return a **200 HTTP response code** to avoid displaying a raw error message.
     - **404 (Not Found)**:
       - Similarly, configured CloudFront to serve `/error404.html` for all **404** errors with a **200 HTTP response code**.
   
### 3. **Invalidate CloudFront Cache (if needed)**
   - In cases where the new settings were not immediately visible, a cache invalidation was performed:
     ```bash
     aws cloudfront create-invalidation --distribution-id YOUR_DISTRIBUTION_ID --paths "/*"
     ```

### 4. **Tested Custom Error Pages**
   - Accessed restricted or non-existent pages to verify that the custom error page is displayed instead of the default XML error messages.

## **Final Result**

The setup now ensures that:
- Users will see the custom `error404.html` page for both **403** (Access Denied) and **404** (Not Found) errors.
- The error pages provide a more user-friendly experience with clear instructions and a way to return to the main site.

---
