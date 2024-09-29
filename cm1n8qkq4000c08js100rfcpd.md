---
title: "Next Cloudinary: A Game-Changer for Client-Side File Handling"
seoTitle: "Next Cloudinary: A Game-Changer for Client-Side File Handling"
seoDescription: "Cloudinary has long been a robust solution for managing assets like images and videos in web applications. Its features allow for smooth asset management"
datePublished: Sun Sep 29 2024 07:09:51 GMT+0000 (Coordinated Universal Time)
cuid: cm1n8qkq4000c08js100rfcpd
slug: next-cloudinary-a-game-changer-for-client-side-file-handling
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1727593301797/56b87688-2471-4e74-9459-8f2353e880a7.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1727593664535/10bbb56b-a20d-49da-af26-9c33f158b2df.webp
tags: programming-blogs, javascript, reactjs, cloudinary, frontend-development, nextjs

---

Cloudinary has long been a robust solution for managing assets like images and videos in web applications. Its features allow for smooth asset management and optimization, but they stepped up their game to accommodate Next.js with a dedicated library called **Next Cloudinary**. After exploring it, I was thoroughly impressed. Although it’s not yet widely used, **Next Cloudinary** is an incredibly powerful tool that integrates perfectly with Next.js applications, making it a must-try for developers looking to streamline their asset management workflows.

### Next Cloudinary `CldUploadWidget`

Next Cloudinary has provided a widget called `CldUploadWidget` which creates a new instance of the [Cloudinary Upload Widget](https://cloudinary.com/documentation/upload_widget) which gives an easy way to add upload capabilities to the Next.js app.

![Next Cloudinary CldUploadWidget](https://cdn.hashnode.com/res/hashnode/image/upload/v1727593553056/62546c2e-230e-48e8-b555-51784b32a530.webp align="center")

Whether the files are stored locally, accessed via URLs, or retrieved from third-party sources like Google Drive, this component can handle them seamlessly. This broad integration means users can interact with various file sources without needing complex configurations on the server.

CldUploadWidget supports two options: signed and unsigned. These options allow us to control the security and restrictions.

### Powerful Image Optimization with `CldImage`

Another component `CldImage` is an evolution of Next.js’s native `<Image />` component. It goes beyond basic image rendering, allowing for advanced optimization, transformations, and real-time manipulations. What sets `CldImage` apart is how easily you can implement image effects like cropping, adding filters, or adjusting colors with just a few props. These enhancements don't just simplify image handling; they also significantly improve application performance by reducing image payloads and enhancing load times—important factors for SEO and user experience.

For example, with `CldImage`, you can add a blur effect, resize images, or apply custom transformations on the fly, which would otherwise require extensive backend processing or third-party image editing tools. Here’s a quick comparison of what makes `CldImage` a 'pro' version of the Next.js `<Image />` tag:

* **Automatic Image Optimization:** Like Next.js’s image component, but with the added flexibility of Cloudinary’s extensive transformations.
    
* **Advanced Effects:** Supports filters, overlays, and cropping using Cloudinary’s powerful API.
    
* **Real-Time Adjustments:** You can tweak images without needing to re-upload or manipulate them manually.
    

This feature set is essential for developers dealing with dynamic content or user-generated uploads, where having tools to manage, optimize, and enhance images can dramatically reduce overhead.

In `CIdImage` component we can render responsive Images just by using the `sizes` prop. With the `sizes` prop, we can configure as we want the sizes for our application, Here is an example:

```javascript
  import { CldImage } from 'next-cloudinary';
 
  <CldImage
    width="960"
    height="600"
    src="<Your Public ID>"
    sizes="(max-width: 768px) 100vw,
          (max-width: 1200px) 50vw,
          33vw"
    alt="Description"
  />
```

This would give us roughly full-width images on mobile, a 2-column layout on tablets, and a 3-column layout on desktop views.

For the above code, the output would look like:

```javascript
<img
  alt="Turtle"
  loading="lazy"
  width="960"
  height="600"
  decoding="async"
  data-nimg="1"
  style="color:transparent"
  sizes="(max-width: 768px) 100vw, (max-width: 1200px) 50vw, 33vw"
  srcset="
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_256/f_auto/q_auto/v1/<Public ID> 256w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_384/f_auto/q_auto/v1/<Public ID> 384w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_640/f_auto/q_auto/v1/<Public ID> 640w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_750/f_auto/q_auto/v1/<Public ID> 750w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_828/f_auto/q_auto/v1/<Public ID> 828w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_1080/f_auto/q_auto/v1/<Public ID> 1080w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_1200/f_auto/q_auto/v1/<Public ID> 1200w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_1920/f_auto/q_auto/v1/<Public ID> 1920w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_2048/f_auto/q_auto/v1/<Public ID> 2048w,
    https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_3840/f_auto/q_auto/v1/<Public ID> 3840w
  "
  src="https://res.cloudinary.com/<Cloud Name>/image/upload/c_limit,w_3840/f_auto/q_auto/v1/<Public ID>"
>
```

Where the image is automatically generated on the fly with Cloudinary by passing in a URL parameter of `w_<width>`.

### Additional Functionalities

`Next Cloudinary` is more than file uploading and image optimization. It offers a range of additional features, like video transformations, responsive media handling, and even watermarking, which makes it incredibly versatile. By directly leveraging Cloudinary’s core strengths in Next.js, you can build highly performant, scalable applications without worrying about intricate asset management.

### A Common Mistake That I Made - Should Be Aware

When configuring **Next Cloudinary** in your project, one easy-to-overlook step involves setting the correct environment variables. Specifically, when you configure Cloudinary with the cloud name, API key, and secret key, make sure that the `cloud_name` and `api_key` values are prefixed with `NEXT_PUBLIC_`. This ensures that they are exposed to both the client and server environments in Next.js.

Here’s the correct way to set up the configuration:

```javascript
cloudinary.config({
    cloud_name: process.env.NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME,
    api_key: process.env.NEXT_PUBLIC_CLOUDINARY_API_KEY,
    api_secret: process.env.CLOUDINARY_API_SECRET,
});
```

If you skip this prefix for the `cloud_name` or `api_key`, you’ll likely encounter an error such as:

```bash
vbnetCopy codeError: A Cloudinary API Key is required for signed requests, please make sure your environment variable is set and configured in your environment.
```

In my case, I mistakenly forgot to add the `NEXT_PUBLIC_` prefix to the API key, leading to the above error. Here's what my incorrect code looked like:

```javascript
cloudinary.config({
    cloud_name: process.env.NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME,
    api_key: process.env.CLOUDINARY_API_KEY,       // Missing NEXT_PUBLIC_ prefix
    api_secret: process.env.CLOUDINARY_API_SECRET,
});
```

Ensuring that the environment variables are correctly prefixed with `NEXT_PUBLIC_` is essential for avoiding such issues when using Cloudinary in both server-side and client-side code.

> Note: If you don't use the NEXT\_PUBLIC\_ you will still be able to get the values ​​on the API route in next js. but according to my research and experience, Next Cloudinary expects the env variable to be with that prefix. So, even if you get the value on the console, still it won't work.

### Resources

* [https://next.cloudinary.dev/](https://next.cloudinary.dev/)
    
* [https://stackoverflow.com/questions/69743178/how-to-fix-cloudinary-error-must-supply-api-key](https://stackoverflow.com/questions/69743178/how-to-fix-cloudinary-error-must-supply-api-key)
    
* [https://community.cloudinary.com/discussion/742/missing-dependency-signed-upload-requires-an-api-key](https://community.cloudinary.com/discussion/742/missing-dependency-signed-upload-requires-an-api-key)