# Security Policy

## Reporting a Vulnerability

If you discover a security issue, avoid posting credentials, personal data, payment information, or exploitable details in a public issue. Use a private contact channel maintained by the repository owner.

## Secret Handling

- Never commit `.env` files.
- Use `.env.example` files only as templates.
- Rotate any credential that is accidentally committed.
- Use Razorpay test credentials during development.
- Use separate production credentials for MongoDB, mail, Cloudinary, and payments.

## Deployment Checklist

- HTTPS enabled
- Strong `JWT_SECRET`
- `NODE_ENV=production`
- `CLIENT_URL` restricted to approved frontend origin(s)
- Database credentials use least privilege
- Payment webhooks and signatures tested
- Dependencies reviewed with `npm audit`
- Production logs checked for sensitive data
