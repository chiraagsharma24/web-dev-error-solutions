# 🐞 Handling Firestore Data Validation for Posts to Prevent Invalid Data


## Description of the Error

A common problem when storing blog posts or other content in Firestore is ensuring data integrity.  Developers often face issues with invalid data being written to the database, leading to unexpected application behavior or crashes. This might involve incorrect data types, missing required fields, or values outside allowed ranges.  For example, attempting to save a post with a negative number of views or a post title exceeding a specified character limit will lead to inconsistent data and potential application errors. This document details how to prevent this by implementing robust data validation before writing to Firestore.

## Step-by-Step Code Fix

This example uses TypeScript and the Firebase Admin SDK.  Adaptations for other languages (e.g., JavaScript) are straightforward.

**1. Define a Post Schema:**

```typescript
interface Post {
  title: string;
  content: string;
  authorId: string;
  views: number;
  createdAt: Date;
  tags?: string[]; // Optional tags
}
```

**2. Create a Validation Function:**

```typescript
function validatePost(post: any): Post | null {
  // Check for required fields
  if (!post.title || !post.content || !post.authorId) {
    console.error("Error: Title, content, and authorId are required.");
    return null;
  }

  // Check data types and ranges
  if (typeof post.title !== 'string' || post.title.length > 100) {
    console.error("Error: Title must be a string under 100 characters.");
    return null;
  }
  if (typeof post.content !== 'string') {
    console.error("Error: Content must be a string.");
    return null;
  }
  if (typeof post.authorId !== 'string') {
    console.error("Error: AuthorId must be a string.");
    return null;
  }
  if (typeof post.views !== 'number' || post.views < 0) {
    console.error("Error: Views must be a non-negative number.");
    return null;
  }
  if (post.tags && !Array.isArray(post.tags)) {
      console.error("Error: Tags must be an array.");
      return null;
  }

  //Data Transformation if needed
  const validatedPost: Post = {
    title: post.title.trim(), //Remove extra spaces
    content: post.content,
    authorId: post.authorId,
    views: post.views || 0, // Default to 0 if views is missing
    createdAt: post.createdAt || new Date(), // Default to current date if missing
    tags: post.tags || [], // Default to empty array if missing
  };
  return validatedPost;
}
```

**3. Integrate Validation into your Firestore Write Operation:**

```typescript
import { getFirestore } from "firebase/firestore";
import { collection, addDoc } from "firebase/firestore";


const db = getFirestore();

async function addPost(post: any) {
  const validatedPost = validatePost(post);
  if (validatedPost) {
    try {
      const docRef = await addDoc(collection(db, "posts"), validatedPost);
      console.log("Document written with ID: ", docRef.id);
    } catch (e) {
      console.error("Error adding document: ", e);
    }
  }
}

// Example usage
const newPost = {
  title: "  My New Post  ",
  content: "This is the content of my post.",
  authorId: "user123",
  views: -5, //Example of invalid data
  tags: "This is not an array" // Example of invalid data
};

addPost(newPost);
```

## Explanation

This code defines a clear schema for posts, enforcing data types and constraints. The `validatePost` function acts as a gatekeeper, checking the incoming data against this schema.  Any invalid data is caught, and an error message is logged to the console. Only valid data passes through and is written to Firestore.  This prevents invalid data from corrupting your database and improves application reliability. The use of optional fields with default values improves the robustness of data handling.


## External References

* [Firebase Firestore Data Types](https://firebase.google.com/docs/firestore/data-model)
* [Firebase Admin SDK](https://firebase.google.com/docs/admin/setup)
* [TypeScript Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

