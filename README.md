# setup-web-projects

A comprehensive guide and collection of setup instructions for modern web development projects. This repository provides detailed instructions for setting up various web development environments and frameworks.

## Features

- **Laravel + Vue.js**: Complete setup guide for Laravel applications with Vue.js integration
- **Next.js + Shadcn**: Modern React setup with Next.js and Shadcn/ui components
- **Starter Kits**: Instructions for using official Laravel starter kits
- **Best Practices**: Development guidelines and best practices for each stack

## Getting Started

Choose the technology stack you want to work with from the sections below. Each section contains detailed setup instructions, configuration guides, and best practices.

## Quick Navigation

[![Tech Stack Navigation](https://raw.githubusercontent.com/aploon/setup-web-projects/main/assets/quickstart.png)](https://github.com/aploon/setup-web-projects#tech-stack-navigation)

> Quickly navigate to your desired technology stack. No need to scroll through the entire document!

## Laravel And Vue.js

### Method 1: Using Laravel UI Package (Recommended for Beginners)

This method uses Laravel's official UI scaffolding package which provides a quick setup with basic authentication and Vue.js integration.

1. Create a new Laravel project:
```bash
composer create-project laravel/laravel your-project-name
cd your-project-name
```

2. Install Laravel UI package:
```bash
composer require laravel/ui
```

3. Generate Vue.js scaffolding:
```bash
php artisan ui vue
```

4. Install NPM dependencies and compile assets:
```bash
npm install
npm run dev
```

5. Start the development server:
```bash
php artisan serve
```

### Method 2: Manual Installation (Advanced Setup)

This method gives you more control over the setup and dependencies.

1. Create a new Laravel project:
```bash
composer create-project laravel/laravel your-project-name
cd your-project-name
```

2. Install Vue.js and other required dependencies:
```bash
npm install vue @vitejs/plugin-vue
```

3. Update your `vite.config.js`:
```javascript
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue({
            template: {
                transformAssetUrls: {
                    base: null,
                    includeAbsolute: false,
                },
            },
        }),
    ],
});
```

4. Create a Vue app entry point in `resources/js/app.js`:
```javascript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

5. Create your main Vue component in `resources/js/App.vue`:
```vue
<template>
    <div>
        <h1>Welcome to Laravel + Vue.js</h1>
    </div>
</template>

<script>
export default {
    name: 'App'
}
</script>
```

6. Update your `resources/views/welcome.blade.php`:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Laravel + Vue.js</title>
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>
<body>
    <div id="app"></div>
</body>
</html>
```

7. Install dependencies and compile assets:
```bash
npm install
npm run dev
```

8. Start the development server:
```bash
php artisan serve
```

### Additional Notes

- For Method 1, the Laravel UI package provides a basic authentication system and Vue.js components out of the box.
- For Method 2, you have more flexibility to choose your own Vue.js components, state management (Vuex/Pinia), and routing solutions.
- Both methods support hot module replacement (HMR) for a better development experience.
- Remember to add `.env` to your `.gitignore` file and configure your database settings in the `.env` file.

### Troubleshooting

If you encounter any issues:

1. Clear Laravel's cache:
```bash
php artisan cache:clear
php artisan config:clear
php artisan view:clear
```

2. Rebuild NPM dependencies:
```bash
rm -rf node_modules
rm package-lock.json
npm install
```

3. Make sure your Node.js version is compatible (Node.js 16+ recommended)

## Laravel Starter kit 

### Introduction

Our Vue starter kit provides a robust, modern starting point for building Laravel applications with a Vue frontend using [Inertia](https://inertiajs.com).

Inertia allows you to build modern, single-page Vue applications using classic server-side routing and controllers. This lets you enjoy the frontend power of Vue combined with the incredible backend productivity of Laravel and lightning-fast Vite compilation.

This starter kit utilizes TypeScript, Tailwind, and the [shadcn-vue](https://www.shadcn-vue.com) component library.

### Installation

To create a new Laravel application using one of our starter kits, follow these steps:

1. First, ensure you have PHP and Composer installed on your system. Then install the Laravel installer CLI tool:

```bash
composer global require laravel/installer
```

2. Create a new Laravel application using the Laravel installer CLI. The installer will prompt you to select your preferred starter kit:

```bash
laravel new my-app
```

3. Navigate to your project directory and install frontend dependencies:

```bash
cd my-app
npm install && npm run build
```

4. Start the Laravel development server:

```bash
composer run dev
```

Your application will be accessible in your web browser at http://localhost:8000.

### Official Documentation

Documentation for all Laravel starter kits can be found on the [Laravel website](https://laravel.com/docs/starter-kits).

### Contributing

Thank you for considering contributing to our starter kit! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

### Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

### License

The Laravel starter kits are open-sourced software licensed under the MIT license.

## Next.js And Shadcn

### Installation and Setup

1. Create a new Next.js project:
```bash
npx create-next-app@latest my-app
```

2. Navigate to your project directory:
```bash
cd my-app
```

3. Initialize Shadcn/ui in your project:
```bash
npx shadcn@latest init
```

During the initialization, you'll be prompted to:
- Choose between a Next.js project or Monorepo
- Select your preferred style (Default or New York)
- Choose your color preferences
- Select the location for your components
- Configure the import alias

### Adding Components

You can add Shadcn/ui components to your project using the following command:

```bash
npx shadcn@latest add button
```

### Using Components

After adding components, you can import and use them in your pages:

```tsx
import { Button } from "@/components/ui/button"
 
export default function Home() {
  return (
    <div>
      <Button>Click me</Button>
    </div>
  )
}
```

### Available Components

Shadcn/ui provides a wide range of components that you can add to your project:

- Button
- Card
- Dialog
- Dropdown Menu
- Input
- Form
- Select
- Tabs
- Toast
- And many more...

To add any component, simply use the `add` command followed by the component name:

```bash
npx shadcn@latest add [component-name]
```

### Best Practices

1. **Component Location**: Keep your components in the `components/ui` directory for better organization
2. **Styling**: Use Tailwind CSS classes for custom styling
3. **TypeScript**: Enable TypeScript for better type safety and developer experience
4. **Theme Customization**: Customize your theme in the `globals.css` file

### Development

Start your development server:

```bash
npm run dev
```

Your application will be available at http://localhost:3000
