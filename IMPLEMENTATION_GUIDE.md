# Contact Us & About Us Implementation Guide

## Contact Us Section - HTML Structure

```html
<section class="section" id="contact">
    <h2>Contact Us</h2>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 50px;">
        <!-- LEFT COLUMN: Contact Form -->
        <div>
            <h3>Send us a Message</h3>
            <form id="contactForm">
                <input type="text" id="contact-name" />
                <input type="email" id="contact-email" />
                <input type="tel" id="contact-phone" />
                <input type="text" id="contact-subject" />
                <textarea id="contact-message"></textarea>
                <button type="submit">Send Message</button>
            </form>
        </div>
        
        <!-- RIGHT COLUMN: Contact Info Cards -->
        <div>
            <h3>Contact Information</h3>
            <div class="info-card">Location</div>
            <div class="info-card">Phone</div>
            <div class="info-card">Email</div>
        </div>
    </div>
</section>
```

## About Us Section - Enhanced

```html
<section class="section" id="about">
    <h2>About Us</h2>
    <p>Main description paragraph...</p>
    
    <!-- NEW: Leadership & Management Section -->
    <div>
        <h3>Leadership & Management</h3>
        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));">
            <!-- Member Card - Clickable to open modal -->
            <div class="about-member" onclick="openModal('memberRajeshModal')">
                <img src="..." alt="Name" />
                <h4>Name</h4>
                <p>Position</p>
                <small>Details</small>
            </div>
        </div>
    </div>
</section>
```

## Member Profile Modal

```html
<div id="memberRajeshModal" class="modal">
    <div class="modal-content member-modal-content">
        <button class="close-btn" onclick="closeModal('memberRajeshModal')">&times;</button>
        <img src="..." alt="Name" />
        <h2>Name</h2>
        <p class="position">Position Title</p>
        <p class="description">Bio/Description</p>
        <div class="contact-details">
            <p><strong>Position:</strong> Title</p>
            <p><strong>Experience:</strong> Years</p>
            <p><strong>Affiliation:</strong> Organization</p>
        </div>
    </div>
</div>
```

## Notification Types

### 1. Phone Notification (Top-Right)
```
✓ APPLICATION RECEIVED
  Rajesh Kumar (Cricket) - Will contact soon
```

### 2. SMS Notification (Bottom-Left)
```
✉ SMS NOTIFICATION
  Confirmation sent to +91 XXXXXXXXXX
```

### 3. Push Notification (Top-Right)
```
🔔 ALERT
  Rajesh Kumar (Cricket) - +91 XXXXXXXXXX
```

## JavaScript Integration Points

### Contact Form Handler
```javascript
document.getElementById('contactForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
        name: document.getElementById('contact-name').value,
        email: document.getElementById('contact-email').value,
        phone: document.getElementById('contact-phone').value,
        subject: document.getElementById('contact-subject').value,
        message: document.getElementById('contact-message').value,
        type: 'Contact Form'
    };
    // Trigger notifications
    showPhoneNotification(formData);
    showSmsNotification(formData);
    showNtfyPushNotification(formData);
    sendNtfyAlert(formData);
});
```

### Member Modal Functions
```javascript
function openModal(modalId) {
    const modal = document.getElementById(modalId);
    modal.classList.add('active');
}

function closeModal(modalId) {
    const modal = document.getElementById(modalId);
    modal.classList.remove('active');
}
```

## CSS Key Classes

| Class | Purpose |
|-------|---------|
| `.about-member` | Committee member card styling |
| `.about-member:hover` | Hover animation (lift effect) |
| `.member-modal-content` | Enhanced modal for member profiles |
| `.member-modal-content img` | Circular member photo |
| `.member-modal-content .position` | Title/position styling |
| `.member-modal-content .description` | Bio text styling |
| `.modal` | Modal background overlay |
| `.modal.active` | Show/hide modal state |
| `.form-group` | Form field wrapper |
| `.form-actions` | Form button container |

## Responsive Breakpoints

### Mobile (< 768px)
- Contact form switches to single column (1fr instead of 1fr 1fr)
- Modal content width: 95%
- Reduced padding: 25px
- Form actions stack vertically
- Member cards stack in single column

### Desktop (≥ 768px)
- Contact form: 2 columns
- Modal content max-width: 600px
- Normal padding: 40px
- Form actions side-by-side
- Member cards: auto-fit grid (200px min)

## Color Scheme

- Primary: `#00bcd4` (Cyan)
- Navy: `#1a3a52`
- Background: `#fff` / `#f8f9fa`
- Text: `#333` / `#555` / `#666`
- Success: `#10b981` (Green)

## SMS Notification Features

✅ Shows when form is submitted
✅ Displays phone number where SMS will be sent
✅ Auto-dismisses after 6 seconds
✅ Green gradient background
✅ Envelope icon (fas fa-envelope)
✅ Smooth slide-in animation from left

## ntfy.sh Integration

### Configuration
- Topic Name: `mac_alerts`
- Full URL: `https://ntfy.sh/mac_alerts`

### Subscription
- Desktop: Visit https://ntfy.sh/mac_alerts
- Mobile: Download ntfy app, subscribe to topic
- Email: Can add email notifications via ntfy dashboard

### Message Format for Contact Forms
```
📧 NEW CONTACT INQUIRY

Name: [Name]
Phone: [Phone]
Email: [Email]
Subject: [Subject]

Message:
[Full Message Content]
```

### Message Format for Applications
```
🏆 NEW [CRICKET/FOOTBALL] APPLICATION

Name: [Name]
Phone: [Phone]
Email: [Email]
```

## Testing Checklist

- [ ] Contact form validates required fields
- [ ] Form submission triggers all 3 notifications
- [ ] SMS notification shows correct phone number
- [ ] Click member card opens correct modal
- [ ] Modal close button works
- [ ] Clicking outside modal closes it
- [ ] Responsive design works on mobile
- [ ] ntfy.sh receives notifications (check topic)
- [ ] Forms reset after submission
- [ ] All links in navigation work

## Future Enhancement Ideas

1. **Backend Integration**: Connect to email service (SendGrid, Mailgun)
2. **SMS Gateway**: Integrate Twilio for actual SMS sending
3. **Contact Form Validation**: Add email verification, phone validation
4. **Member Search**: Add search/filter for committee members
5. **Contact Form Analytics**: Track submissions by date/type
6. **Auto-Reply Email**: Send automatic confirmation email to user
7. **Admin Dashboard**: View all submissions in a dashboard
8. **Form Captcha**: Add reCAPTCHA for spam prevention

