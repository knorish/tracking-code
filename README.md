# Tracking Code Repository

This repository contains code snippets for tracking various user events across web applications using popular analytics platforms. These snippets are designed to be integrated into Knorish sites for comprehensive event tracking and analytics.

## Overview

The tracking code snippets in this repository enable tracking of various user interactions such as signups, checkout initiation, and purchases. They are formatted for easy integration with platforms like Google Analytics and Facebook Pixel (Meta Pixel).

## File Naming Convention

Files in this repository follow a consistent naming pattern to make it easy to identify their purpose:

```
[context]-[event]-[event-type]-[platform].txt
```

Where:
- **context**: Where the code is implemented (e.g., `global`, `thankyou-page`)
- **event**: The user action being tracked (e.g., `signup`, `initiatecheckout`, `purchase`)
- **event-type**: Type of tracking (e.g., `tracking`, `custom-events-tracking`)
- **platform**: The analytics platform (e.g., `google-analytics`, `facebook-pixel`)

## Supported Platforms

### Google Analytics

The repository includes tracking code for Google Analytics 4 (GA4) using the Global Site Tag (gtag.js) implementation. These snippets enable tracking standard and custom events.

### Facebook Pixel (Meta Pixel)

The repository includes tracking code for Facebook's Pixel (Meta Pixel) to track standard events like PageView, Purchase, and InitiateCheckout, as well as custom events.

## Supported Events

The following events are supported:

1. **Signup**: Track new user registrations
2. **InitiateCheckout**: Track when users begin the checkout process
3. **Purchase**: Track completed purchases and transaction details

## How to Use

1. Choose the appropriate tracking code file based on the event you want to track and the platform you're using.
2. Copy the code from the file.
3. Replace the placeholder variables (enclosed in `{{}}`) with dynamic values from your application.
4. Insert the code snippet in the appropriate location in your HTML.

### Placeholder Variables

The tracking code snippets contain placeholder variables that should be replaced with actual values:

- `{{userid}}`: User's unique identifier
- `{{name}}`: User's name
- `{{email}}`: User's email address
- `{{item_id}}`: Product/course ID
- `{{item_name}}`: Product/course name
- `{{price}}` or `{{totalpaid}}`: Price or total amount paid
- `{{currency}}`: Currency code (e.g., INR, USD)
- `{{orderid}}`: Order or transaction ID

### Implementation Examples

#### Example 1: Tracking a signup event with Google Analytics

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-QKQDYW9XXX"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag() { dataLayer.push(arguments); }
    gtag('js', new Date());
    gtag('config', 'G-QKQDYW9XXX');

    gtag("event", "signup_on_knorish_site", {
        userid: "12345",
        username: "John Doe",
        email: "john.doe@example.com"
    });
</script>
```

#### Example 2: Tracking a purchase event with Facebook Pixel

```html
<!-- Meta Pixel Code -->
<script>
    !function (f, b, e, v, n, t, s) {
        if (f.fbq) return; n = f.fbq = function () {
            n.callMethod ?
            n.callMethod.apply(n, arguments) : n.queue.push(arguments)
        };
        if (!f._fbq) f._fbq = n; n.push = n; n.loaded = !0; n.version = '2.0';
        n.queue = []; t = b.createElement(e); t.async = !0;
        t.src = v; s = b.getElementsByTagName(e)[0];
        s.parentNode.insertBefore(t, s)
    }(window, document, 'script', 'https://connect.facebook.net/en_US/fbevents.js');
    fbq('init', '780682850594XXX');
    fbq('track', 'PageView');
    fbq('track', 'Purchase',
    {
        value: 99.99,
        currency: 'USD',
        content_type: 'product',
        contents: [
        {
            id: 'COURSE-123',
            quantity: 1
        }]
    });
</script>
<noscript><img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=780682850594XXX&ev=PageView&noscript=1" /></noscript>
```

## Important Notes

1. Replace the tracking IDs (`G-QKQDYW9XXX` for Google Analytics and `780682850594XXX` for Facebook Pixel) with your actual tracking IDs.
2. Ensure all placeholder variables are replaced with actual values before deploying to production.
3. The examples use masked tracking IDs (ending with XXX) for security reasons. Use your actual tracking IDs in implementation.

## Requirements

- These code snippets are designed to be integrated into HTML web pages.
- They require an active internet connection to load the necessary JavaScript libraries.
- You need valid tracking IDs for Google Analytics and/or Facebook Pixel to use these snippets.

## Privacy Considerations

When implementing these tracking codes, ensure compliance with privacy regulations such as GDPR, CCPA, etc. Consider:

1. Obtaining user consent before loading tracking scripts
2. Updating your privacy policy to reflect the data collection practices
3. Implementing data anonymization where required by law