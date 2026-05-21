# Modern React & Appwrite Blog Application

A premium, full-featured blog application built with **React**, **Vite**, **Tailwind CSS v4**, **Redux Toolkit**, and **Appwrite Cloud Services**. This app features secure authentication, responsive layouts, rich text editing, automated slugs, dynamic image previews, and flexible post management.

---

## 🚀 Key Features

- **Secure Authentication**: Register and login securely using Appwrite Auth APIs.
- **Rich Text Editor**: Integrated with **TinyMCE** for advanced article formatting (lists, tables, links, alignments, styles).
- **Automated Slug Generation**: Title inputs dynamically transform into SEO-friendly URL slugs.
- **State Management**: Built on **Redux Toolkit** to manage user session states smoothly.
- **Responsive Layout**: Designed with fluid layouts and custom styling utilizing Tailwind CSS.
- **Protected Layouts**: Custom `AuthLayout` middleware protects routes (Add, Edit, and View posts) depending on session status.
- **Fail-Safe Image Processing**: Integrated live image previews for selected files and robust URL parsing for Appwrite storage buckets.
- **Secure Actions**: Warning confirmation prompts protect critical actions (like deleting posts).

---

## 🛠️ Tech Stack

- **Core**: React (v18), Vite (v6), JavaScript (ES6+)
- **Styling**: Tailwind CSS (v4) with `@tailwindcss/vite`
- **Routing**: React Router DOM (v7)
- **State Management**: Redux Toolkit & React Redux
- **Backend Services**: Appwrite Cloud (Auth, Databases, and Storage)
- **Form Controls**: React Hook Form & HTML React Parser
- **Rich Text Editor**: TinyMCE React Integration

---

## ⚙️ Environment Configuration

To run this application, create a `.env` file in the root directory (using `.env.sample` as a guide) and populate it with your Appwrite project credentials and TinyMCE API key:

```env
VITE_APPWRITE_URL="https://cloud.appwrite.io/v1"
VITE_APPWRITE_PROJECT_ID="your_appwrite_project_id"
VITE_APPWRITE_DATABASE_ID="your_appwrite_database_id"
VITE_APPWRITE_COLLECTION_ID="your_appwrite_collection_id"
VITE_APPWRITE_BUCKET_ID="your_appwrite_bucket_id"

# TinyMCE API Key (free from tiny.cloud)
VITE_TINY_MCE_API_KEY="your_tinymce_api_key"
```

---

## 🔒 Crucial Database & Storage Setup

To ensure that the application loads and displays images correctly without browser security blocks (such as **OpaqueResponseBlocking** or **CORB**), configure your Appwrite Cloud console as follows:

### 1. Storage Bucket Permissions (Required)
For the application to fetch and render post images in `<img>` tags:
1. Open your **Appwrite Console** and select **Storage** from the sidebar.
2. Select your blog storage bucket.
3. Click on the **Settings** tab.
4. Under the **Permissions** section, click **Add Permission**.
5. Select **Any** (or `role:all`).
6. Check **Read** permission.
7. Click **Update** to save.

### 2. Database Indexes (Required)
If you wish to use the `active` post filter on the Home page:
1. Select **Databases** -> **your_database** -> **your_collection** -> **Indexes**.
2. Click **Create Index**.
3. Set the key to `status`, type to **Key**, and order to **ASC** or **DESC**.
4. Click **Create**.

---

## 📦 Getting Started

### 1. Clone & Install Dependencies
```bash
# Clone the repository and enter the directory
cd myBlogApp

# Install npm packages
npm install
```

### 2. Run the Development Server
```bash
npm run dev
```
Open [http://localhost:5173](http://localhost:5173) in your browser to view the application.

### 3. Build for Production
To build a highly optimized bundle for production:
```bash
npm run build
```

---

## 📂 Project Structure

```text
myBlogApp/
├── public/                 # Static assets
├── src/
│   ├── appwrite/           # Appwrite configurations & services (auth, databases, storage)
│   ├── components/         # Base & layout components (Header, Footer, Button, RTE, Input, Select, etc.)
│   ├── conf/               # Safe environment variable configuration manager
│   ├── pages/              # Page components (Home, AddPost, EditPost, Login, AllPosts, etc.)
│   ├── store/              # Redux store configurations & slices (authSlice)
│   ├── App.jsx             # Main router root layout component
│   ├── index.css           # Global stylesheet importing Tailwind CSS v4
│   └── main.jsx            # Entry point rendering RouterProvider
├── index.html              # HTML shell
├── vite.config.js          # Vite config bundling Tailwind v4 & React
└── package.json            # Scripts and dependencies
```
