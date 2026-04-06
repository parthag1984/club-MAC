# JavaScript Functions Reference

## Modal Management

### openModal(modalId)
```javascript
function openModal(modalId) {
    const modal = document.getElementById(modalId);
    modal.classList.add('active');
}
```
**Purpose:** Opens a modal by adding 'active' class
**Parameters:** modalId (string) - ID of modal to open
**Example:** `openModal('memberRajeshModal')`

### closeModal(modalId)
```javascript
function closeModal(modalId) {
    const modal = document.getElementById(modalId);
    modal.classList.remove('active');
}
```
**Purpose:** Closes a modal by removing 'active' class
**Parameters:** modalId (string) - ID of modal to close
**Example:** `closeModal('memberRajeshModal')`

### Click Outside to Close
```javascript
window.onclick = function(event) {
    if (event.target.classList.contains('modal')) {
        event.target.classList.remove('active');
    }
}
```
**Purpose:** Automatically close modal when clicking outside content area
**Triggers:** On any window click event

---

## Form Submission Handlers

### Cricket Form Submission
```javascript
document.getElementById('cricketForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
        name: document.getElementById('cricket-name').value,
        email: document.getElementById('cricket-email').value,
        phone: document.getElementById('cricket-contact').value,
        type: 'Cricket'
    };
    showPhoneNotification(formData);
    showSmsNotification(formData);
    showNtfyPushNotification(formData);
    sendNtfyAlert(formData);
    alert('Thank you for your cricket application! We will contact you soon.');
    closeModal('cricketFormModal');
    this.reset();
});
```

### Football Form Submission
```javascript
document.getElementById('footballForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
        name: document.getElementById('football-name').value,
        email: document.getElementById('football-email').value,
        phone: document.getElementById('football-contact').value,
        type: 'Football'
    };
    showPhoneNotification(formData);
    showSmsNotification(formData);
    showNtfyPushNotification(formData);
    sendNtfyAlert(formData);
    alert('Thank you for your football application! We will contact you soon.');
    closeModal('footballFormModal');
    this.reset();
});
```

### Contact Form Submission
```javascript
if (document.getElementById('contactForm')) {
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
        showPhoneNotification(formData);
        showSmsNotification(formData);
        showNtfyPushNotification(formData);
        sendNtfyAlert(formData);
        alert('Thank you for contacting us! We will get back to you shortly.');
        this.reset();
    });
}
```

---

## Notification Functions

### showPhoneNotification(formData)
```javascript
function showPhoneNotification(formData) {
    let notification = document.getElementById('phone-notification');
    if (!notification) {
        notification = document.createElement('div');
        notification.id = 'phone-notification';
        notification.innerHTML = `
            <div class="notification-icon">
                <i class="fas fa-check-circle"></i>
            </div>
            <div class="notification-body">
                <div class="notification-title">MESSAGE RECEIVED</div>
                <div class="notification-text" id="notification-message"></div>
            </div>
            <button class="notification-close" onclick="closeNotification()">
                <i class="fas fa-times"></i>
            </button>
        `;
        document.body.appendChild(notification);
    }

    // Update notification content
    const message = formData.type === 'Contact Form' 
        ? `${formData.name} - ${formData.subject}` 
        : `${formData.name} (${formData.type}) - Will contact soon`;
    
    document.getElementById('notification-message').textContent = message;

    // Show notification
    notification.classList.add('show');

    // Auto close after 5 seconds
    setTimeout(() => {
        notification.classList.remove('show');
    }, 5000);
}
```

**Purpose:** Display application received notification
**Location:** Top-right corner
**Auto-closes:** 5 seconds
**Parameters:** formData (object)
  - name (string)
  - type (string) - 'Cricket', 'Football', or 'Contact Form'
  - subject (string, optional)

### closeNotification()
```javascript
function closeNotification() {
    const notification = document.getElementById('phone-notification');
    if (notification) {
        notification.classList.remove('show');
    }
}
```

**Purpose:** Manually close phone notification
**Triggers:** Manual click on close button

### showSmsNotification(formData)
```javascript
function showSmsNotification(formData) {
    let smsNotif = document.getElementById('sms-notification');
    if (!smsNotif) {
        smsNotif = document.createElement('div');
        smsNotif.id = 'sms-notification';
        smsNotif.innerHTML = `
            <i class="fas fa-envelope"></i>
            <div id="sms-notification-text">
                <div id="sms-notification-title">SMS NOTIFICATION</div>
                <div id="sms-notification-message"></div>
            </div>
        `;
        document.body.appendChild(smsNotif);
    }

    // Update SMS notification content
    const message = formData.type === 'Contact Form'
        ? `Contact inquiry received. SMS sent to ${formData.phone}`
        : `Confirmation sent to ${formData.phone}`;
    
    document.getElementById('sms-notification-title').textContent = 'SMS NOTIFICATION';
    document.getElementById('sms-notification-message').textContent = message;

    // Show SMS notification
    smsNotif.classList.add('show');

    // Auto close after 6 seconds
    setTimeout(() => {
        smsNotif.classList.remove('show');
    }, 6000);
}
```

**Purpose:** Display SMS notification
**Location:** Bottom-left corner
**Auto-closes:** 6 seconds
**Parameters:** formData (object)
  - phone (string)
  - type (string)
**Message Format:**
  - Contact Form: "Contact inquiry received. SMS sent to [phone]"
  - Applications: "Confirmation sent to [phone]"

### showNtfyPushNotification(formData)
```javascript
function showNtfyPushNotification(formData) {
    let ntfyNotif = document.getElementById('ntfy-push-notification');
    if (!ntfyNotif) {
        ntfyNotif = document.createElement('div');
        ntfyNotif.id = 'ntfy-push-notification';
        ntfyNotif.innerHTML = `
            <div class="ntfy-push-icon">
                <i class="fas fa-bell"></i>
            </div>
            <div class="ntfy-push-body">
                <div class="ntfy-push-title">ALERT</div>
                <div class="ntfy-push-message" id="ntfy-push-message"></div>
            </div>
            <button class="ntfy-push-close" onclick="closeNtfyNotification()">
                <i class="fas fa-times"></i>
            </button>
        `;
        document.body.appendChild(ntfyNotif);
    }

    // Update ntfy notification content
    document.getElementById('ntfy-push-message').textContent =
        `${formData.name} (${formData.type}) - ${formData.phone}`;

    // Show ntfy notification
    ntfyNotif.classList.add('show');

    // Auto close after 7 seconds
    setTimeout(() => {
        ntfyNotif.classList.remove('show');
    }, 7000);
}
```

**Purpose:** Display ntfy.sh push notification
**Location:** Top-right corner
**Auto-closes:** 7 seconds
**Parameters:** formData (object)
  - name (string)
  - type (string)
  - phone (string)

### closeNtfyNotification()
```javascript
function closeNtfyNotification() {
    const ntfyNotif = document.getElementById('ntfy-push-notification');
    if (ntfyNotif) {
        ntfyNotif.classList.remove('show');
    }
}
```

**Purpose:** Manually close ntfy.sh notification
**Triggers:** Manual click on close button

---

## API Integration

### sendNtfyAlert(formData)
```javascript
function sendNtfyAlert(formData) {
    const ntfyTopic = 'mac_alerts'; // ntfy.sh topic

    let message, title;
    if (formData.type === 'Contact Form') {
        title = `Contact Form Submission`;
        message = `📧 NEW CONTACT INQUIRY\n\nName: ${formData.name}\nPhone: ${formData.phone}\nEmail: ${formData.email}\nSubject: ${formData.subject}\n\nMessage:\n${formData.message}`;
    } else {
        title = `${formData.type} Coaching Camp Application`;
        message = `🏆 NEW ${formData.type.toUpperCase()} APPLICATION\n\nName: ${formData.name}\nPhone: ${formData.phone}\nEmail: ${formData.email}`;
    }

    // Send to ntfy.sh
    fetch(`https://ntfy.sh/${ntfyTopic}`, {
        method: 'POST',
        headers: {
            'Content-Type': 'text/plain',
            'Title': title
        },
        body: message
    })
    .then(response => {
        console.log('✅ ntfy.sh Alert Sent Successfully');
        console.log('Topic:', ntfyTopic);
        console.log('Title:', title);
        console.log('Message:', message);
    })
    .catch(error => {
        console.error('Error sending ntfy.sh alert:', error);
    });
}
```

**Purpose:** Send form submission to ntfy.sh service
**API Endpoint:** `https://ntfy.sh/mac_alerts`
**Method:** POST
**Headers:** 
  - Content-Type: text/plain
  - Title: Subject line for notification
**Parameters:** formData (object)
**Console Output:** Success/error logs

**Contact Form Message Format:**
```
📧 NEW CONTACT INQUIRY

Name: [Name]
Phone: [Phone]
Email: [Email]
Subject: [Subject]

Message:
[Full message content]
```

**Application Message Format:**
```
🏆 NEW [CRICKET/FOOTBALL] APPLICATION

Name: [Name]
Phone: [Phone]
Email: [Email]
```

---

## Form Download Functions

### downloadForm(sport)
```javascript
function downloadForm(sport) {
    const formContent = sport === 'cricket' ? getCricketFormHTML() : getFootballFormHTML();
    const element = document.createElement('a');
    element.setAttribute('href', 'data:text/html;charset=utf-8,' + encodeURIComponent(formContent));
    element.setAttribute('download', `Majilpur_${sport.charAt(0).toUpperCase() + sport.slice(1)}_Application_Form.html`);
    element.style.display = 'none';
    document.body.appendChild(element);
    element.click();
    document.body.removeChild(element);
}
```

**Purpose:** Download form as HTML file
**Parameters:** sport (string) - 'cricket' or 'football'
**Filename Format:** `Majilpur_Cricket_Application_Form.html` or `Majilpur_Football_Application_Form.html`

### getCricketFormHTML()
```javascript
function getCricketFormHTML() {
    return `<!DOCTYPE html>...`; // Returns HTML string
}
```

**Purpose:** Generate cricket form HTML for download
**Returns:** HTML string with complete cricket application form

### getFootballFormHTML()
```javascript
function getFootballFormHTML() {
    return `<!DOCTYPE html>...`; // Returns HTML string
}
```

**Purpose:** Generate football form HTML for download
**Returns:** HTML string with complete football application form

---

## Event Listeners

### Form Submit Events
- `cricketForm` - ID for cricket application form
- `footballForm` - ID for football application form
- `contactForm` - ID for contact us form

### Modal Click Events
- `openModal('memberRajeshModal')` - Opens Rajesh Kumar profile
- `openModal('memberPriyaModal')` - Opens Priya Patel profile
- `openModal('cricketFormModal')` - Opens cricket application form
- `openModal('footballFormModal')` - Opens football application form

### Window Events
- `window.onclick` - Closes modal when clicking outside

---

## Data Flow Diagram

```
Form Submission
    ↓
preventDefault()
    ↓
Collect Form Data
    ↓
┌─────────────────────────────────────┐
│ Show 3 Notifications Simultaneously │
├─────────────────────────────────────┤
│ 1. showPhoneNotification()           │
│ 2. showSmsNotification()            │
│ 3. showNtfyPushNotification()       │
└─────────────────────────────────────┘
    ↓
Send to ntfy.sh
    ↓
sendNtfyAlert(formData)
    ↓
fetch() POST request
    ↓
Display Alert
    ↓
Close Modal (if applicable)
    ↓
Reset Form
```

---

## Debugging Console Logs

### ntfy.sh Success
```
✅ ntfy.sh Alert Sent Successfully
Topic: mac_alerts
Title: Contact Form Submission
Message: [Full message content]
```

### ntfy.sh Error
```
Error sending ntfy.sh alert: [Error Details]
```

---

## Form Data Object Structure

### Contact Form Data
```javascript
{
    name: "John Doe",
    email: "john@example.com",
    phone: "+91 9876543210",
    subject: "Inquiry About Cricket Program",
    message: "I am interested in joining...",
    type: "Contact Form"
}
```

### Cricket Application Data
```javascript
{
    name: "John Doe",
    email: "john@example.com",
    phone: "+91 9876543210",
    type: "Cricket"
}
```

### Football Application Data
```javascript
{
    name: "John Doe",
    email: "john@example.com",
    phone: "+91 9876543210",
    type: "Football"
}
```

---

## Notification Timing

| Notification | Duration | Delay | Trigger |
|--------------|----------|-------|---------|
| Phone (top-right) | 5 seconds | Immediate | Form submit |
| SMS (bottom-left) | 6 seconds | Immediate | Form submit |
| Push (top-right) | 7 seconds | Immediate | Form submit |
| ntfy.sh | Variable | ~1 second | Form submit |

---

## Error Handling

### Try-Catch Not Used
- ntfy.sh fetch uses `.catch()` instead
- Form validation relies on HTML5 `required` attribute
- No explicit error handling for missing elements

### Potential Issues to Monitor
1. Missing ntfy.sh topic subscription
2. Slow internet connection (ntfy.sh delay)
3. Browser blocking fetch requests (CORS)
4. Missing notification elements in DOM

---

## Browser Compatibility

- **ES6 Features Used:** 
  - Arrow functions `=>`
  - Template literals `` ` ``
  - `const` and `let`
  - Fetch API

- **Minimum Browser Requirements:**
  - Chrome 51+
  - Firefox 54+
  - Safari 10+
  - Edge 15+
  - IE 11 (partial support, fetch polyfill needed)

---

## Performance Considerations

1. **DOM Creation:** Notifications created once, then reused
2. **Event Listeners:** Added once during page load
3. **Fetch Requests:** Non-blocking, background process
4. **Auto-close Timeouts:** Cleared automatically

---

## Security Notes

1. **No Server-side Validation** - All validation client-side
2. **No CSRF Protection** - Form not submitted to server
3. **No Rate Limiting** - Multiple rapid submissions allowed
4. **No Input Sanitization** - Data sent as-is to ntfy.sh
5. **Data Visibility** - Message content visible in browser console

---

## Future Enhancement Code Templates

### Email Confirmation
```javascript
function sendConfirmationEmail(formData) {
    // Requires backend service
    fetch('/api/send-email', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(formData)
    });
}
```

### SMS Integration (Twilio)
```javascript
function sendSMS(formData) {
    fetch('/api/send-sms', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            phone: formData.phone,
            message: 'Thank you for contacting MAC!'
        })
    });
}
```

### Database Storage
```javascript
function saveFormData(formData) {
    fetch('/api/save-submission', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(formData)
    });
}
```

