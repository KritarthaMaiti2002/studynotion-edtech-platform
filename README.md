# StudyNotion EdTech Platform

StudyNotion is a full-stack edtech application with student, instructor, and admin-oriented flows. The project includes course discovery and enrollment, authentication, instructor course management, user profiles, reviews, payment integration, email workflows, media uploads, and course-progress tracking.

> **Repository note:** This codebase was originally created in 2023 and uses Create React App / React 18 on the frontend and Express / MongoDB on the backend. It is kept intentionally close to the original implementation instead of being rewritten into a newer framework.

## Features

- Email/OTP signup and JWT-based authentication
- Student, instructor, and admin authorization flows
- Course catalog and course detail pages
- Instructor course creation, editing, sections, and subsections
- Student cart, enrollment, and course-progress tracking
- Razorpay payment integration
- Ratings and reviews
- Profile management and password reset
- Cloudinary-backed media uploads
- Contact and transactional email flows
- Responsive React UI with Redux Toolkit and Tailwind CSS

## Tech Stack

### Frontend
- React 18
- Create React App / react-scripts 5
- React Router
- Redux Toolkit
- Tailwind CSS
- Axios
- Chart.js

### Backend
- Node.js
- Express
- MongoDB / Mongoose
- JWT authentication
- Cloudinary
- Razorpay
- Nodemailer

## Project Structure

```text
.
├── public/                 # CRA public assets
├── src/                    # React application
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── slices/
│   └── data/
├── server/                 # Express API
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   └── utils/
├── .env.example            # Frontend environment template
└── package.json
```

## Local Setup

### Prerequisites

- Node.js 16.18+ (the original project pins Node 16.18.0 in `.nvmrc`)
- npm
- MongoDB
- Cloudinary account for media uploads
- Mail server credentials for OTP/email features
- Razorpay credentials for payment flows

### 1. Clone the repository

```bash
git clone REPLACE_WITH_YOUR_GITHUB_REPOSITORY_URL
cd studynotion-edtech-project
```

### 2. Configure the frontend

Copy `.env.example` to `.env` and set the backend API base URL.

```bash
cp .env.example .env
```

Example:

```env
REACT_APP_BASE_URL=http://localhost:4000/api/v1
```

### 3. Configure the backend

Copy `server/.env.example` to `server/.env` and fill in the required values.

```bash
cp server/.env.example server/.env
```

Required groups include:

- `JWT_SECRET`
- `MONGODB_URL`
- mail credentials
- Cloudinary credentials
- Razorpay credentials
- `CLIENT_URL` for CORS

Never commit real `.env` files or credentials.

### 4. Install dependencies

Frontend/root:

```bash
npm install
```

Backend:

```bash
cd server
npm install
cd ..
```

### 5. Run the application

Run frontend and backend together:

```bash
npm run dev
```

Or separately:

```bash
npm start
```

```bash
npm run server
```

Default development URLs are typically:

- Frontend: `http://localhost:3000`
- Backend: `http://localhost:4000`

## Production / Deployment Notes

Before deploying:

1. Set a strong production `JWT_SECRET`.
2. Restrict `CLIENT_URL` to the deployed frontend origin. Multiple origins can be comma-separated.
3. Use production MongoDB, Cloudinary, mail, and Razorpay credentials.
4. Serve both frontend and backend over HTTPS.
5. Review authentication/token storage for your production threat model. The original frontend stores its JWT in browser local storage in addition to the backend cookie flow.
6. Run dependency/security audits and test payment flows using provider test credentials before enabling live payments.

## Security Notes

- Real secrets are intentionally excluded from Git.
- `.env` files are ignored; `.env.example` files document required variables.
- Backend CORS is restricted through `CLIENT_URL` instead of a wildcard origin.
- Authentication cookies use `httpOnly`, environment-aware `secure`, and `sameSite` settings.
- This is an older learning/demo codebase and should receive a dedicated security review before handling real customer data or live payments.

## Known Technical Debt

- Create React App / `react-scripts` is an older frontend toolchain.
- The historical `.nvmrc` uses Node 16.18.0. A runtime upgrade should be tested separately rather than mixed into repository cleanup.
- The codebase contains legacy debug logging and commented debug statements that can be reduced further.
- Authentication currently includes both cookie and local-storage token usage; a future hardening pass should standardize the strategy.
- No automated test suite or CI workflow was included in the original project.

## Attribution and License

The backend `package.json` in the supplied source names **Saikat Mukherjee** as its author and declares the backend package as `ISC`. No repository-level `LICENSE` file was present in the supplied archive.

Before publishing this repository publicly, verify the original source/course/tutorial license and preserve any attribution that it requires. Do not remove third-party attribution unless you are certain you have the right to do so.

## Status

Repository cleanup completed for GitHub preparation. A full dependency install/build should still be run in the target development environment before the first public release.
