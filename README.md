# Cloud Resume Template

This repository contains a template for creating a Cloud Resume website. The template is designed to be simple, yet comprehensive, allowing you to showcase your skills, experience, projects, and more. It uses Tailwind CSS for styling, making it easy to customize.

## Demo

Check out the live demo of the resume website: [https://aasmasayyad.com/](https://aasmasayyad.com/)

## How to Use

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-github-username/cloud-resume-template.git
   cd cloud-resume-template
   ```

2. **Customize `index.html`:**

   Open `index.html` and replace the placeholders with your information.

3. **Deploy to AWS S3:**

   - Create a new S3 bucket (use same name as your website domain if you have one):

     ```bash
     aws s3 mb s3://your-resume-website-name
     ```

   - Enable static website hosting on the bucket. Go to the S3 console, select your bucket, go to the "Properties" tab, and enable "Static website hosting". Set the index document to `index.html`.

   - Upload your website files to the S3 bucket:

     ```bash
     aws s3 sync . s3://your-resume-website-name --exclude ".git/*"
     ```

   - Make your bucket public. Go to the S3 console, select your bucket, go to the "Permissions" tab, and add a bucket policy like this. Be sure to change the bucket name in the policy code below:

     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Sid": "PublicReadGetObject",
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::your-resume-website-name/*"
         }
       ]
     }
     ```

4. **Access your website:**

   Your resume website is now live at `http://your-resume-website-name.s3-website.your-region.amazonaws.com`

5. **Want to add a favicon?:**

    Generate one easily here [Simple Favicon Generator](https://riyazsayyad.com/generate-favicon.html)

## Want to Learn AWS Cloud?

If you want to learn more about AWS Cloud, check out [needforcloud.com](https://needforcloud.com) to kickstart your journey.
