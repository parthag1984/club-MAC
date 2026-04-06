# CSS Classes & Styling Reference

## New CSS Classes Added

### Modal Styling
```css
.member-modal-content {
    background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
    padding: 50px 40px;
    border-radius: 12px;
    text-align: center;
    box-shadow: 0 15px 50px rgba(0,0,0,0.2);
    border-top: 5px solid #00bcd4;
}

.member-modal-content img {
    width: 140px;
    height: 140px;
    border-radius: 50%;
    object-fit: cover;
    border: 4px solid #00bcd4;
    margin-bottom: 25px;
    box-shadow: 0 8px 25px rgba(0, 188, 212, 0.3);
}

.member-modal-content h2 {
    color: #1a3a52;
    font-size: 1.8em;
    margin-bottom: 10px;
    font-weight: 700;
}

.member-modal-content .position {
    color: #00bcd4;
    font-weight: 700;
    font-size: 1.1em;
    margin-bottom: 15px;
}

.member-modal-content .description {
    color: #666;
    line-height: 1.8;
    margin-bottom: 20px;
    max-width: 500px;
    margin-left: auto;
    margin-right: auto;
}

.member-modal-content .contact-details {
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    margin-top: 25px;
    border-left: 4px solid #00bcd4;
}

.member-modal-content .contact-details p {
    margin: 8px 0;
    color: #555;
}
```

### Member Card Styling
```css
.about-member {
    cursor: pointer !important;
}

.about-member:hover {
    transform: translateY(-8px) !important;
    box-shadow: 0 12px 30px rgba(0, 188, 212, 0.2) !important;
}

/* Inline styles in HTML */
style="text-align: center; padding: 20px; background-color: #f8f9fa; 
       border-radius: 8px; transition: transform 0.3s, box-shadow 0.3s;"
```

### Modal Content Styling
```css
.modal-content {
    background-color: #fff;
    padding: 40px;
    border-radius: 10px;
    width: 90%;
    max-width: 600px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.3);
    max-height: 90vh;
    overflow-y: auto;
    animation: slideIn 0.3s;
    border-top: 5px solid #00bcd4;  /* NEW: Added blue top border */
}
```

### Modal Header Styling
```css
.modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
    border-bottom: 2px solid #e0e0e0;  /* Changed from #00bcd4 */
    padding-bottom: 15px;
}

.modal-header h2 {
    color: #1a3a52;
    font-family: 'Cormorant Garamond', serif;  /* Updated */
    margin: 0;
    font-size: 1.8em;
    font-weight: 600;  /* Updated */
}
```

---

## Form Styling (Already Existed, Enhanced)

### Form Group
```css
.form-group {
    margin-bottom: 20px;
}

.form-group label {
    display: block;
    margin-bottom: 8px;
    color: #1a3a52;
    font-weight: 600;
}

.form-group input,
.form-group textarea {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-family: 'Lato', sans-serif;
    font-size: 1em;
    transition: border-color 0.3s;
}

.form-group input:focus,
.form-group textarea:focus {
    outline: none;
    border-color: #00bcd4;
    box-shadow: 0 0 8px rgba(0,188,212,0.2);
}
```

### Form Actions
```css
.form-actions {
    display: flex;
    gap: 15px;
    margin-top: 30px;
}

.form-actions .btn {
    flex: 1;
    text-align: center;
    padding: 12px 20px;
}
```

---

## Notification Styling

### Phone Notification (Top-Right)
```css
#phone-notification {
    position: fixed;
    top: 24px;
    right: 24px;
    z-index: 9999;
    background: #ffffff;
    border-radius: 14px;
    box-shadow: 0 12px 40px rgba(26,43,74,0.18), 0 2px 8px rgba(0,0,0,0.08);
    border: 1.5px solid rgba(16,185,129,0.25);
    padding: 18px 28px 18px 20px;
    display: flex;
    align-items: center;
    gap: 14px;
    min-width: 320px;
    max-width: 440px;
    transition: transform 0.45s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.35s ease;
    opacity: 0;
    pointer-events: none;
    transform: translateX(420px);
}

#phone-notification.show {
    opacity: 1;
    pointer-events: all;
    transform: translateX(0);
}

.notification-icon {
    width: 44px;
    height: 44px;
    flex-shrink: 0;
    background: rgba(16,185,129,0.12);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    color: #059669;
}

.notification-title {
    font-family: 'Lato', sans-serif;
    font-weight: 700;
    font-size: 13px;
    color: #059669;
    margin-bottom: 3px;
    letter-spacing: 0.2px;
}

.notification-text {
    font-size: 12px;
    color: #555;
}
```

### SMS Notification (Bottom-Left)
```css
#sms-notification {
    position: fixed;
    bottom: 30px;
    left: 30px;
    z-index: 9999;
    background: linear-gradient(135deg, #10b981, #059669);
    color: white;
    padding: 16px 24px;
    border-radius: 10px;
    font-size: 14px;
    font-weight: 700;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
    display: flex;
    align-items: center;
    gap: 12px;
    min-width: 280px;
    max-width: 380px;
    transform: translateX(-420px);
    transition: transform 0.45s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.35s ease;
    opacity: 0;
    pointer-events: none;
}

#sms-notification.show {
    opacity: 1;
    pointer-events: all;
    transform: translateX(0);
}

#sms-notification i {
    color: white;
    font-size: 16px;
}

#sms-notification-text {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 3px;
}

#sms-notification-title {
    font-weight: 700;
    font-size: 12px;
    letter-spacing: 0.5px;
}

#sms-notification-message {
    font-weight: 400;
    font-size: 13px;
    opacity: 0.95;
}
```

### ntfy.sh Push Notification (Top-Right)
```css
#ntfy-push-notification {
    position: fixed;
    top: 30px;
    right: 30px;
    z-index: 9999;
    background: linear-gradient(135deg, #3b82f6, #1e40af);
    color: white;
    padding: 18px 24px 18px 20px;
    border-radius: 12px;
    font-size: 13px;
    font-weight: 600;
    box-shadow: 0 10px 40px rgba(59, 130, 246, 0.4);
    display: flex;
    align-items: center;
    gap: 14px;
    min-width: 320px;
    max-width: 420px;
    transform: translateX(450px);
    transition: transform 0.45s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.35s ease;
    opacity: 0;
    pointer-events: none;
}

#ntfy-push-notification.show {
    opacity: 1;
    pointer-events: all;
    transform: translateX(0);
}

.ntfy-push-icon {
    width: 48px;
    height: 48px;
    flex-shrink: 0;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    color: white;
    border: 2px solid rgba(255, 255, 255, 0.3);
}

.ntfy-push-body {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 2px;
}

.ntfy-push-title {
    font-weight: 700;
    font-size: 12px;
    letter-spacing: 1px;
    text-transform: uppercase;
    opacity: 0.9;
}

.ntfy-push-message {
    font-weight: 400;
    font-size: 13px;
    opacity: 0.95;
    line-height: 1.4;
}

.ntfy-push-close {
    background: none;
    border: none;
    cursor: pointer;
    color: rgba(255, 255, 255, 0.7);
    font-size: 18px;
    padding: 4px;
    line-height: 1;
    transition: color 0.2s;
    flex-shrink: 0;
}

.ntfy-push-close:hover {
    color: white;
}
```

---

## Animations

### Fade In
```css
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.modal {
    animation: fadeIn 0.3s;
}
```

### Slide In
```css
@keyframes slideIn {
    from {
        transform: translateY(-50px);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

.modal-content {
    animation: slideIn 0.3s;
}
```

### Notification Slide In/Out
- SMS: Slides from left (`translateX(-420px)` to `translateX(0)`)
- Phone: Slides from right (`translateX(420px)` to `translateX(0)`)
- Push: Slides from right (`translateX(450px)` to `translateX(0)`)

---

## Responsive Design Media Query

```css
@media (max-width: 768px) {
    /* Contact form - single column layout */
    #contact > div {
        grid-template-columns: 1fr !important;
        gap: 30px !important;
    }

    /* Member cards - single column */
    .about-member {
        margin-bottom: 20px;
    }

    /* Modal sizing */
    .modal-content {
        width: 95%;
        padding: 25px;
    }

    /* Form actions - stack vertically */
    .form-actions {
        flex-direction: column;
    }
}
```

---

## Color Variables (CSS Variables)

```css
:root {
    --navy: #1a3a52;
    --navy-dark: #0f1c30;
    --gold: #d4a574;
    --gold-light: #e8c96b;
    --white: #ffffff;
    --off-white: #f8f6f1;
    --gray-light: #f0eff0;
    --gray: #888;
    --text: #333;
    --shadow: 0 8px 32px rgba(26,43,74,0.13);
    --radius: 12px;
    --transition: 0.3s ease;
}
```

---

## Button Styling

### Primary Button
```css
.btn-primary {
    background: linear-gradient(135deg, var(--gold), var(--gold-light));
    color: var(--navy);
    box-shadow: 0 8px 20px rgba(201,168,76,0.3);
    position: relative;
    overflow: hidden;
}

.btn-primary:hover {
    background: linear-gradient(135deg, var(--gold-light), #f4e4a6);
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(201,168,76,0.45);
}
```

### Outline Button
```css
.btn-outline {
    background: transparent;
    color: var(--gold);
    border: 2px solid var(--gold);
    transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.btn-outline:hover {
    background: var(--gold);
    color: var(--navy);
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(201,168,76,0.35);
}
```

### Secondary Button
```css
.btn-secondary {
    display: inline-block;
    padding: 12px 28px;
    background-color: #ddd;
    color: #1a3a52;
    text-decoration: none;
    border-radius: 4px;
    font-weight: 600;
    transition: all 0.3s;
    border: 2px solid #ddd;
    cursor: pointer;
}

.btn-secondary:hover {
    background-color: #1a3a52;
    color: white;
}
```

---

## Contact Form Grid Layout

```css
/* Contact section - 2 column grid */
#contact > div {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 50px;
    max-width: 1000px;
    margin: 0 auto;
}

/* Contact info cards */
div style="background-color: #f8f9fa; padding: 25px; border-radius: 8px; margin-bottom: 20px;"
```

---

## About Section Member Grid

```css
/* Member grid - auto-fit responsive */
div style="display: grid; 
          grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); 
          gap: 30px; 
          max-width: 900px; 
          margin: 0 auto;"
```

---

## Close Button Styling

```css
.close-btn {
    font-size: 28px;
    font-weight: bold;
    color: #1a3a52;
    cursor: pointer;
    background: none;
    border: none;
    transition: color 0.3s;
}

.close-btn:hover {
    color: #00bcd4;
}
```

---

## Font Families Used

- **Headings:** Cormorant Garamond (serif)
- **Body Text:** Lato (sans-serif)
- **Display:** Montserrat (sans-serif)
- **Form Labels:** Lato (sans-serif)

---

## Transition & Duration Timings

| Effect | Duration | Easing |
|--------|----------|--------|
| SMS Slide In/Out | 0.45s | cubic-bezier(0.34, 1.56, 0.64, 1) |
| Notification Auto Close | 5-7s | - |
| Modal Fade | 0.3s | ease |
| Modal Slide | 0.3s | - |
| Hover Effects | 0.3s | ease |
| Notification Fade | 0.35s | ease |

---

## Z-Index Stack

| Element | Z-Index | Notes |
|---------|---------|-------|
| Modal Background | 2000 | Highest |
| Notifications | 9999 | Above modals |
| Header | 1000 | Fixed position |
| Normal Content | 1 | Default |


