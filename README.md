# Vocation Chrome Extension

A powerful Chrome extension that streamlines the job search process by automating cover letter generation, outreach messages, and application tracking.

[View Portfolio](https://zachayers.io) | [Chrome Web Store](https://chrome.google.com/webstore)

## About

Vocation is a comprehensive job search assistant that lives in your browser. Built with Vue.js and modern web technologies, it integrates seamlessly with popular job boards to enhance productivity. Features intelligent templates for cover letters and outreach messages, tracks applications across multiple platforms, and offers metrics to optimize your job search strategy.

## Built With

- Vue.js 3
- Chrome Extension Manifest V3
- Webpack
- TailwindCSS
- Chrome Storage API
- Background Service Workers

## Features

- **Smart Templates** - Pre-built templates for cover letters, LinkedIn messages, and follow-ups
- **Job Board Integration** - Works with Indeed, LinkedIn, Glassdoor, AngelList, and 20+ platforms
- **Application Tracking** - Save jobs, track application status, and manage your pipeline
- **Metrics Dashboard** - Visualize application stats, response rates, and search progress
- **Personal Info Management** - Store and auto-fill your professional details
- **Overlay Interface** - Non-intrusive UI that appears when needed
- **Cross-Site Functionality** - Works seamlessly across all job search websites

## Supported Platforms

LinkedIn Jobs, Indeed, Glassdoor, AngelList, Monster, ZipRecruiter, Dice, SimplyHired, CareerBuilder, Hired, Wellfound, RemoteOK, We Work Remotely, FlexJobs, Upwork, Toptal, Guru, Freelancer, Fiverr, PeoplePerHour

## Getting Started

### Prerequisites

- Chrome Browser
- Node.js 14.x or higher

### Installation for Development

```bash
git clone https://github.com/N73311/vocation-chrome.git
cd vocation-chrome
npm install
npm run build
```

### Loading in Chrome

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable "Developer mode"
3. Click "Load unpacked"
4. Select the `dist` folder

### Development

```bash
npm run dev    # Start development with hot reload
npm run build  # Build for production
npm run test   # Run tests
```

## Project Structure

```
vocation-chrome/
├── src/
│   ├── background/     # Service worker scripts
│   ├── content/        # Content scripts for job sites
│   ├── popup/          # Extension popup UI
│   ├── overlay/        # Overlay interface components
│   └── utils/          # Shared utilities
├── public/             # Static assets
└── manifest.json       # Extension manifest
```

## Privacy & Security

- All data stored locally using Chrome Storage API
- No external servers or data collection
- Permissions only for job board domains
- Open source and auditable

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

## Author

Zachariah Ayers - [zachayers.io](https://zachayers.io)