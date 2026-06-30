# Testing Workflow

name: Example

on:
  push:
    branches: [ testing ]


<!-- Print Somthing -->
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - name: Print
        run: echo "Hello World"
      - name: Print
        run: echo "::debug::This is a debug message"


    # Print repo details using normal console log
    steps:
      - name: Print repo details
        run: |
          echo "Owner: ${{ github.repository_owner }}"
          echo "Repo: ${{ github.event.repository.name }}"
          echo "Event: ${{ github.event_name }}"
          echo "Branch: ${{ github.ref }}"
          echo "Actor: ${{ github.actor }}"
          echo "SHA: ${{ github.sha }}"
          echo "Token: ${{ secrets.GITHUB_TOKEN }}"


<!-- Build node project -->
jobs:
  example:
    runs-on: ubuntu-latest
    # Build Project
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v6

      - name: Install dependencies
        run: npm ci

      - name: Build project
        run: npm run build
