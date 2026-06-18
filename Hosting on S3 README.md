<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Ephraim Quaye  
**Email:** quayeephraim5@gmail.com

---

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to host a static website using Amazon S3. I'm doing this project to learn how to configure S3 buckets for public web hosting, upload files, and enable static website hosting – all without needing a web server.

### Tools and concepts

The main service I used was Amazon S3 specifically for storing website files, enabling static hosting, and managing access permissions. Key concepts I learned include bucket policies and ACLs for controlling access, the importance of making objects publicly readable, and how S3 generates a bucket endpoint URL to serve your site. I also got hands-on with troubleshooting like fixing the 403 Forbidden error which really helped solidify how permissions and hosting work together.

### Time, challenges, and wins

This project took me approximately 1 hour and 15 minutes in total, including the setting up of the bucket policy. The most challenging part was definitely troubleshooting the 403 Forbidden error I had enabled static hosting but forgot to make the files public, so I spent a bit of time figuring out why my site wasn't loading. It was most rewarding to finally see my website live after applying the bucket policy and ACLs that moment when the page loaded properly made all the effort worth it.

---

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I will create an S3 bucket to store all the files (HTML, CSS, images, etc.) for my website, because S3 provides a simple, scalable, and cost-effective way to host static content without needing a traditional web server.

### How long it took to create the bucket

Creating an S3 bucket took me about 5–10 minutes in total. Since this was my first time navigating the S3 console, I spent a few extra minutes carefully reading through each option and configuration setting to make sure I understood what I was doing. I wanted to ensure I wasn't just clicking through mindlessly especially since I was dealing with public access settings and permissions. The actual creation itself was quick, but I took my time to absorb the information along the way.

### Region selection

The Region I picked for my S3 bucket was Cape Town (af-south-1) because it's geographically closest to me, which helps reduce latency and improve load times for visitors in my area. Plus, staying within the same region can help keep data transfer costs lower.

### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means my bucket name can't be the same as anyone else's on the entire planet  not even in a different region or account. So I had to get a bit creative with my naming instead of just using something basic like 'my-website.' I ended up going with something that includes my name to make sure it's one of a kind

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step, I will download the website files including the HTML document and a zip folder of images and upload them into my S3 bucket. I'm doing this because these files form the actual content of my static website, and they need to be stored in S3 so they can be served to visitors when they access my bucket's website endpoint. Essentially, I'm populating my storage space with the assets that will make my website functional and visually complete.

### Files I uploaded

I uploaded two files to my S3 bucket – they were an HTML file (which serves as the main structure and content of my webpage) and a zip folder containing images (which provides all the visual assets like photos, icons, and graphics used on the site). The HTML file is what browsers actually read and render when someone visits my website, while the images bring the page to life and make it visually engaging.

### How the files work together

Both files are necessary for this project as they work together to form a complete, functional website. The HTML file provides the structural foundation it defines the layout, text content, and how different elements are organised on the page. The images, on the other hand, serve as the visual components that bring the design to life. When a user visits the website, their browser loads the HTML file, which then references and displays the images from the zip folder. Without the HTML, the images would just be standalone files with no context or structure. Without the images, the HTML would render as a plain, text-heavy page with no visual appeal. In essence, the HTML is the skeleton, and the images are the skin and clothing both are essential for a complete and engaging user experience.

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will enable static website hosting on my S3 bucket and then visit the public URL to see my website live. I'm doing this because, while I've successfully uploaded my HTML and image files, they aren't automatically accessible to the public yet. I need to explicitly configure the bucket to serve content as a website and generate a public endpoint that users can navigate to. This is the defining moment where my bucket transitions from being just a storage container to an actual, live website.

### Understanding website hosting

Website hosting means storing all the files, data, and content that make up a website on a server that is continuously connected to the internet. This allows users from anywhere in the world to access the website simply by entering its URL into their browser. In simpler terms, hosting is like renting digital space where your website actually 'lives' without it, your HTML files, images, and other assets would just exist on your local machine, accessible only to you. With hosting, those files are served to anyone who visits your site, making it publicly available around the clock.

### How I enabled website hosting

To enable website hosting with my S3 bucket, I navigated to the Properties tab of my bucket in the S3 console. From there, I scrolled down to the Static website hosting section and clicked Edit. I then selected the option to Enable static website hosting. After that, I specified the Index document as index.html  which tells S3 which file to serve when someone visits the root of my website URL. I also had the option to specify an Error document (like error.html), which I could customise later if needed. Once I saved these settings, AWS generated a public endpoint URL for my bucket, which I could then use to access my live website.

### Access Control Lists (ACLs)

An ACL is basically a permission system that decides who can access my files and what they can do with them – like view, edit, or delete. Think of it as a bouncer at a club, but for each individual file in my S3 bucket.

I ended up enabling ACLs for this project because the instructions wanted me to learn how they work. Plus, since I'm planning to host a website, I need to make sure my HTML and image files are readable by the public. Even though AWS recommended using bucket policies instead (and I can see why – they're way simpler for making everything public at once), I wanted to understand the more detailed control first. It feels like learning to drive manual before switching to automatic. More work now, but I'll be glad I know it later

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is essentially the public-facing identity of my website. It's what I'll share with colleagues, add to my portfolio, or use to test my site before considering a custom domain. Having it automatically generated makes the process seamless I don't have to configure DNS or buy a domain upfront just to see my site live. It gives me immediate visibility, which is perfect for learning and prototyping.

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I encountered a 403 Forbidden error. At first, I was confused because I had already uploaded my HTML and image files and enabled static website hosting. However, the reason for this error became clear once I reviewed the permissions settings my bucket and its contents were not yet publicly accessible. By default, S3 blocks all public access to ensure security, so even though the hosting feature was enabled, visitors couldn't actually see my files. The solution was to adjust the bucket's permissions by adding a bucket policy that grants public read access to all objects within the bucket.

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I will make my website files publicly accessible by updating the access settings of the objects in my S3 bucket using ACLs. I'm doing this because, while I had already enabled static website hosting, the files themselves remained private by default which was the root cause of the 403 Forbidden error I encountered earlier. By granting public read access to my HTML and image files, I'm ensuring that anyone who visits my bucket endpoint URL can actually view the content. Once this is done and I refresh the endpoint, my website should load fully with all images and styling intact marking the moment my site officially goes live

### How I resolved the 403 error

To resolve this 403 Forbidden error, I updated the access settings of the files inside my bucket by using ACLs to make them publicly readable. While I had already enabled static website hosting, the individual files themselves remained private by default which meant that even though the hosting infrastructure was in place, visitors couldn't actually view the content. By granting public read access to my HTML and image files via ACLs, I ensured that anyone visiting my bucket endpoint could view the website. Once I applied these changes and refreshed the URL, the page loaded successfully with all content displayed correctly.

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension, I'm about to implement a bucket policy that explicitly denies delete permissions on my index.html file. I'm doing this so that I can understand how bucket policies work at a deeper level and see firsthand how they can be used to protect critical website assets from accidental or malicious deletion. This builds on my earlier work with ACLs by introducing a more powerful and flexible tool for managing access control. It also serves as a valuable security exercise ensuring that my website's core file remains safe even if other permissions are misconfigured.

### Understanding bucket policies

A bucket policy is a JSON document that controls access to an entire S3 bucket and everything inside it. The benefit is that you can apply permissions at scale one rule covers everything, instead of setting permissions file by file like with ACLs. ACLs are still useful when you need to manage access at the individual object level, but bucket policies are cleaner and more powerful for bucket-wide controls.

![Image](http://learn.nextwork.org/secure_silver_beautiful_unicorn/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

A bucket policy is a JSON document that controls access to an entire S3 bucket and everything inside it. The benefit is that you can apply permissions at scale – one rule covers everything, instead of setting permissions file by file like with ACLs. ACLs are still useful when you need to manage access at the individual object level, but bucket policies are cleaner and more powerful for bucket-wide controls.

---

---
