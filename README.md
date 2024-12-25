# Scientific Calculator

This is a simple scientific calculator application built using HTML, TailwindCSS, and JavaScript. The purpose of this project is to showcase the process of continuous deployment using GitHub Actions to GitHub Pages.

## Features

- **Basic mathematical operations:** addition, subtraction, multiplication, and division.
- **Advanced scientific functions:** sine, cosine, tangent, logarithm, exponential, and more.
- **Responsive and user-friendly interface:** styled using TailwindCSS.
- **Continuous and automated deployment:** powered by GitHub Actions.

## Technologies Used

- **HTML5:** Defines the structure of the application.
- **TailwindCSS:** Provides fast, responsive styling.
- **JavaScript:** Implements the calculator's functionality.
- **GitHub Actions:** Enables CI/CD for automated deployment to GitHub Pages.

## Project Structure

```
scientific-calculator/
├── public/
│   ├── index.html
│   ├── app.js
├── .github/
│   └── workflows/
│       └── deploy.yml
├── README.md
└── LICENSE
```

## Continuous Deployment with GitHub Actions

This project employs GitHub Actions for continuous deployment to GitHub Pages. Whenever a push is made to the `main` branch, the workflow is triggered, deploying files from the `public` folder to the `gh-pages` branch.

### Workflow Configuration

The GitHub Actions configuration file (`.github/workflows/deploy.yml`) is set up as follows:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.ACTIONS_DEPLOY_TOKEN }}
          publish_branch: gh-pages
          publish_dir: ./public

      - name: Notify deployment success
        if: success()
        run: echo "🚀 Deployment to GitHub Pages was successful!"
```
