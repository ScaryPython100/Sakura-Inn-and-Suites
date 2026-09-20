# Sakura Inn and Suites - Hotel Management System

Guest room service request portal and real-time staff management system for **Sakura Inn and Suites**.

## How It Works

1. **Guest Room Service (QR Code)**:
   - Each hotel room has a unique QR code linking directly to `/room/:roomNumber`.
   - Guests scan the QR code using any smartphone camera to open the service request portal.
   - Guests can select requested amenities, request housekeeping, request supplies, or enter special notes.

2. **Automated Staff & Owner Notifications**:
   - Submissions trigger an email alert via Resend directly to the owner and supervisor emails configured in `RESEND_TO_EMAILS`.
   - The notification email includes a direct link button to open the live Staff Dashboard.

3. **Real-Time Staff Dashboard (`/staff`)**:
   - Real-time live synchronization of incoming room requests across all devices powered by Supabase.
   - Requests can be marked as completed or dismissed.
   - Durable items (e.g. Iron Box, Hair Dryer, Teakettle, Adapters) are automatically moved to the **Borrowed Items** tab to ensure staff collect them back before checkout.
   - Once collected, staff mark the item returned, returning it to inventory.

4. **Service & Inventory Settings (`/staff/settings`)**:
   - Manage real-time availability (available vs out-of-service) and stock limits for each amenity item.
   - Protected by a secure Superhost PIN.

5. **Room Management (`/staff/rooms`)**:
   - View all rooms and print room QR code cards.

## Setup & Environment Variables

Create a `.env` file based on `.env.example`:

```env
# RESEND NOTIFICATION CONFIGURATION
RESEND_API_KEY="re_..."
RESEND_TO_EMAILS="supervisor@sakurainn.com, owner@sakurainn.com"
RESEND_FROM_EMAIL="Sakura Inn and Suites Concierge <onboarding@resend.dev>"

# SUPABASE CONFIGURATION
SUPABASE_URL="https://your-project.supabase.co"
SUPABASE_SERVICE_ROLE_KEY="eyJhbGci..."
SUPABASE_ANON_KEY="eyJhbGci..."

# APP URL (Vercel deployment URL)
APP_URL="https://your-sakura-inn-app.vercel.app"
```

## Running Locally

```bash
npm install
npm run dev
```

## Deployment

Deploy directly to [Vercel](https://vercel.com) by connecting this GitHub repository and configuring the environment variables in your Vercel Project Settings.
