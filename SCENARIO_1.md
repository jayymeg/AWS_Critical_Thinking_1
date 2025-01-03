# SCENARIO 1

As a senior DevOps engineer, you are tasked with designing a solution to ensure users in two different geographical locations, India and London, have a good browsing experience with minimal latency. Create an infrastructure solution that optimizes performance and minimizes latency for users in both regions. Consider factors such as content delivery networks (CDNs), edge caching, global load balancing, and region-specific deployment strategies to achieve this goal effectively. After designing the solutions (use draw.io), implement them and create the infrastructure in your AWS console.

---

## SERVERLESS SOLUTION

### STEP 1: Prepare the Application

- Create a basic HTML file for your static website. (`index.html`)

---

### STEP 2: Host the Static Website on Amazon S3

1. **Create an S3 bucket:**
   - Choose the region closest to users in **India** and **London** (e.g., *Europe (Frankfurt) `eu-central-1`*).
   
2. **Upload the website files:**
   - Upload the `index.html` file to the S3 bucket.
   
3. **Enable static website hosting:**
   - Configure the bucket to host a static website.
   
4. **Make the bucket public:**
   - Ensure the bucket permissions allow public access to the website.

---

### STEP 3: Set up Amazon CloudFront

1. **Create a CloudFront Distribution:**
   - Set the *Origin Domain Name* to the S3 bucket’s website endpoint.
   
2. **Latency Optimization:**
   - CloudFront automatically uses edge locations closest to users for low latency.
   - Users in **India** will use nearby edge locations, while those in **London** will use European edge locations.

---

### STEP 4: Configure DNS with Route 53

1. **Create a Hosted Zone:**
   - Navigate to Route 53 and create a hosted zone for your domain.

2. **Add DNS Records:**
   - Create a **CNAME Record** pointing to the CloudFront domain name.
   - Use **Latency Routing Policy** to optimize the user experience for **India** and **London**.

---

### STEP 5: Monitor and Optimize

- Use **Amazon CloudWatch** to monitor latency and request patterns.

---

## BENEFITS OF THIS SERVERLESS SOLUTION

- **Scalable:** Automatically handles any traffic load.
- **Low Maintenance:** No servers to manage.
- **Cost-Effective:** Pay only for what you use.
- **High Performance:** Utilizes CloudFront's global edge network.

---

This approach is simple, fully serverless, and ideal for minimizing latency across regions.
