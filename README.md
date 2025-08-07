# Vocation Chrome Extension

A powerful Chrome extension that streamlines the job search process by automating cover letter generation, outreach messages, and application tracking. Built with Vue.js and modern web technologies, Vocation integrates seamlessly with popular job boards to enhance productivity.

## Overview

Vocation is a comprehensive job search assistant that lives in your browser. It provides intelligent templates for cover letters and outreach messages, tracks your applications across multiple job boards, and offers metrics to optimize your job search strategy. The extension features a sleek overlay interface that appears on job listing pages, allowing you to save positions, generate customized content, and manage your entire job search workflow without leaving the browser.

## Features

### Core Functionality

- **Smart Templates** - Pre-built templates for cover letters, LinkedIn messages, and follow-ups
- **Job Board Integration** - Works with Indeed, LinkedIn, Glassdoor, AngelList, and 20+ platforms
- **Application Tracking** - Save jobs, track application status, and manage your pipeline
- **Metrics Dashboard** - Visualize application stats, response rates, and search progress
- **Personal Info Management** - Store and auto-fill your professional details
- **Overlay Interface** - Non-intrusive UI that appears when needed
- **Cross-Site Functionality** - Works seamlessly across all job search websites

### Supported Job Boards

- LinkedIn Jobs
- Indeed
- Glassdoor
- AngelList
- Monster
- ZipRecruiter
- Dice
- SimplyHired
- The Muse
- We Work Remotely
- Stack Overflow Jobs
- And many more...

## Installation

### From Chrome Web Store (Recommended)

1. Visit the Chrome Web Store
2. Search for "Vocation Job Search Assistant"
3. Click "Add to Chrome"
4. Grant necessary permissions

### Development Installation

```bash
# Clone the repository
git clone https://github.com/N73311/vocation-chrome.git
cd vocation-chrome

# Install dependencies
npm install
# or
yarn install

# Build for development (with hot reload)
npm run dev
# or
yarn dev

# Build for production
npm run build
# or
yarn build
```

### Loading in Chrome

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable "Developer mode" in the top right
3. Click "Load unpacked"
4. Select the `dist` folder from the build output
5. The extension icon will appear in your toolbar

## Project Structure

```
vocation-chrome/
├── src/
│   ├── assets/             # Icons and images
│   │   └── Icons/          # Job board and feature icons
│   ├── components/         # Vue components
│   │   ├── ButtonDock/     # Floating action buttons
│   │   ├── SideBars/       # Side panel components
│   │   │   ├── JobBoard/   # Job listing management
│   │   │   ├── Metrics/    # Analytics dashboard
│   │   │   ├── Personal/   # User profile settings
│   │   │   └── Templates/  # Message templates
│   │   └── Shared/         # Reusable components
│   ├── overlay/            # Content script overlay
│   ├── popup/              # Extension popup window
│   ├── store/              # Vuex state management
│   └── manifest.json       # Chrome extension manifest
├── public/                 # Static assets
│   ├── icons/              # Extension icons
│   └── _locales/           # Internationalization
└── vue.config.js           # Vue CLI configuration
```

## Usage Guide

### Getting Started

1. **Initial Setup**: Click the Vocation icon and fill in your personal information
2. **Browse Jobs**: Navigate to any supported job board
3. **Save Positions**: Click the floating save button on job listings
4. **Generate Content**: Use templates to create customized messages
5. **Track Applications**: Monitor your progress in the metrics dashboard

### Key Features

#### Job Saving
```javascript
// Automatically detects job details from the page
const jobData = {
    title: extractedTitle,
    company: extractedCompany,
    location: extractedLocation,
    url: window.location.href,
    savedDate: new Date()
};
```

#### Template System
```javascript
// Dynamic template variables
{
    companyName: "{{company}}",
    position: "{{position}}",
    userName: "{{name}}",
    customField: "{{custom}}"
}
```

### Keyboard Shortcuts

- `Ctrl/Cmd + Shift + V` - Toggle Vocation overlay
- `Ctrl/Cmd + S` - Save current job listing
- `Ctrl/Cmd + T` - Open templates panel
- `Esc` - Close any open panel

## Development

### Technology Stack

- **Vue.js 2.6** - Component framework
- **Vuex** - State management
- **Vue Router** - Navigation
- **Chrome Extension API** - Browser integration
- **Webpack** - Module bundling
- **SCSS** - Styling

### Building Components

```vue
<template>
    <div class="job-card">
        <h3>{{ job.title }}</h3>
        <p>{{ job.company }}</p>
        <button @click="saveJob">Save</button>
    </div>
</template>

<script>
export default {
    props: ['job'],
    methods: {
        saveJob() {
            this.$store.dispatch('saveJob', this.job);
        }
    }
}
</script>
```

### State Management

```javascript
// Vuex store modules
const store = {
    modules: {
        jobBoard: jobBoardStore,
        personalInfo: personalInfoStore,
        companyInfo: companyInfoStore,
        gui: guiStore
    }
};
```

## Configuration

### Manifest Permissions

```json
{
    "permissions": [
        "storage",
        "tabs",
        "activeTab"
    ],
    "content_scripts": [{
        "matches": ["<all_urls>"],
        "js": ["js/main.js"],
        "run_at": "document_idle"
    }]
}
```

### User Settings

Settings are stored in Chrome's sync storage:

```javascript
chrome.storage.sync.set({
    personalInfo: {
        name: "John Doe",
        email: "john@example.com",
        linkedIn: "linkedin.com/in/johndoe"
    },
    preferences: {
        autoSave: true,
        showMetrics: true
    }
});
```

## Best Practices

### Performance

- Lazy load components for faster initial load
- Use Chrome storage API efficiently
- Minimize content script footprint
- Debounce user input events

### Security

- Never store sensitive data in plain text
- Validate all user inputs
- Use Chrome's permission system appropriately
- Follow Content Security Policy guidelines

## Troubleshooting

### Common Issues

1. **Extension not appearing**: Check if it's enabled in chrome://extensions
2. **Job detection failing**: Some sites may need custom selectors
3. **Storage quota exceeded**: Clear old saved jobs
4. **Overlay not showing**: Check for CSS conflicts with the host page

### Debug Mode

```javascript
// Enable debug logging
localStorage.setItem('vocation_debug', 'true');

// View logs in console
console.log('[Vocation]', debugInfo);
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow Vue.js style guide
- Write unit tests for new features
- Update documentation
- Test on multiple job board sites

## Future Enhancements

- AI-powered cover letter suggestions
- Interview scheduling integration
- Resume keyword optimization
- Salary research tools
- Application follow-up reminders
- Mobile companion app

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Vue.js team for the excellent framework
- Chrome Extensions documentation
- Job board APIs and documentation
- Open source icon contributors
