# StudyNotion EdTech Platform

StudyNotion is a full-stack EdTech application built with React, Node.js, Express, and MongoDB.

The platform supports student and instructor workflows including authentication, course discovery, course creation and management, enrollment, payments, reviews, profile management, media uploads, email notifications, and course progress tracking.

> **Project note:** This project was originally developed using the Create React App ecosystem and has been retained close to its original architecture rather than being rewritten into a newer framework.

---

## Features

### Authentication and User Management

- Email and OTP-based signup
- JWT authentication
- Login and logout
- Password reset
- Role-based access for students, instructors, and admins
- Profile management

### Student Features

- Browse available courses
- View course details
- Add courses to cart
- Purchase courses using Razorpay
- Access enrolled courses
- Track course progress
- Submit ratings and reviews

### Instructor Features

- Create and manage courses
- Add course sections and subsections
- Upload course media
- Edit existing courses
- View instructor course information
- Manage published course content

### Additional Features

- Cloudinary media uploads
- Razorpay payment integration
- Nodemailer-based email workflows
- Course ratings and reviews
- Responsive user interface
- Redux-based application state management

---

## Tech Stack

### Frontend

- React 18
- Create React App
- React Router
- Redux Toolkit
- Tailwind CSS
- Axios
- Chart.js
- Swiper

### Backend

- Node.js
- Express
- MongoDB
- Mongoose
- JSON Web Tokens
- bcryptjs
- Cloudinary
- Razorpay
- Nodemailer

---

## Project Structure

```text
.
├── public/                 # Frontend public assets
├── src/                    # React application
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── slices/
│   ├── hooks/
│   ├── utils/
│   └── data/
│
├── server/                 # Express backend
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── mail/
│   └── utils/
│
├── .env.example            # Frontend environment template
├── package.json
└── README.md
```

---

## Local Setup

### Prerequisites

You will need:

- Node.js 16.18 or later
- npm
- MongoDB
- Cloudinary account
- Email/SMTP credentials
- Razorpay account for payment testing

The project includes an `.nvmrc` file containing the original Node.js version used by the project.

### 1. Clone the Repository

```bash
git clone https://github.com/KritarthaMaiti2002/studynotion-edtech-platform.git
cd studynotion-edtech-platform
```

### 2. Install Frontend Dependencies

From the project root:

```bash
npm install
```

### 3. Configure the Frontend Environment

Create a `.env` file from the provided example:

```bash
cp .env.example .env
```

Example:

```env
REACT_APP_BASE_URL=http://localhost:4000/api/v1
```

### 4. Install Backend Dependencies

```bash
cd server
npm install
cd ..
```

### 5. Configure the Backend Environment

Create `server/.env` using `server/.env.example` as the template.

The backend requires values for items such as:

```env
PORT=4000
NODE_ENV=development
CLIENT_URL=http://localhost:3000

JWT_SECRET=
MONGODB_URL=

MAIL_HOST=
MAIL_USER=
MAIL_PASS=

CLOUD_NAME=
API_KEY=
API_SECRET=
FOLDER_NAME=studynotion

RAZORPAY_KEY=
RAZORPAY_SECRET=
```

Never commit real credentials or `.env` files to Git.

### 6. Run the Application

Run the frontend and backend together:

```bash
npm run dev
```

Or run them separately.

Frontend:

```bash
npm start
```

Backend:

```bash
npm run server
```

Default local URLs:

- Frontend: `http://localhost:3000`
- Backend: `http://localhost:4000`

---

## Build Verification

The frontend production build has been successfully tested using:

```bash
npm run build
```

The project currently compiles successfully.

Backend JavaScript entry points and updated authentication/mail utility files have also been syntax-checked successfully.

---

## Security

This repository does not contain production credentials.

- Real `.env` files are excluded from Git
- Environment templates are provided through `.env.example`
- Backend CORS uses the configured `CLIENT_URL`
- Authentication cookies use `httpOnly`
- Production cookie security settings depend on the environment
- Password hashing uses `bcryptjs`

Before using the project with real users or live payments, a dedicated production security review is recommended.

See [SECURITY.md](SECURITY.md) for additional information.

---

## Production Considerations

Before deploying this application:

1. Use a strong production `JWT_SECRET`.
2. Configure the correct production MongoDB database.
3. Configure Cloudinary credentials.
4. Configure a production mail provider.
5. Configure Razorpay production credentials only after testing the payment flow.
6. Restrict `CLIENT_URL` to approved frontend origins.
7. Serve both frontend and backend over HTTPS.
8. Review token storage and authentication strategy before handling sensitive user data.

---

## Known Technical Debt

This project intentionally retains parts of its original architecture.

Some areas that could be modernized in a future version include:

- replacing Create React App with a newer frontend build system;
- upgrading the historical Node.js runtime target;
- adding automated tests;
- adding CI/CD workflows;
- standardizing authentication token handling;
- further reducing legacy debug and commented code;
- migrating remaining dependencies from the older CRA toolchain.

These items were kept outside the current repository-cleanup scope to avoid unnecessary changes to the original application architecture.

---

## Repository Validation

During GitHub preparation:

- frontend dependencies were installed successfully;
- backend dependencies were installed successfully;
- the frontend production build completed successfully;
- backend syntax checks passed;
- unused frontend dependencies were removed;
- Swiper was updated;
- backend Cloudinary, Nodemailer, and Nodemon dependencies were updated;
- real environment files were confirmed absent from the repository;
- Git secret checks identified only placeholder/example values.

---

## Attribution and License

The backend package metadata in the original source identifies **Saikat Mukherjee** as the author and declares the backend package under the **ISC** license.

No repository-level `LICENSE` file was included in the original supplied project.

Any attribution or licensing requirements associated with the original project, tutorial, course, or source material should be preserved.

---

## Repository

GitHub: https://github.com/KritarthaMaiti2002/studynotion-edtech-platform

---

## Status

The repository has been cleaned, dependency-checked, build-verified, and prepared for GitHub portfolio use.

Further development can focus on testing, deployment, UI improvements, and modernization of the frontend toolchain.
