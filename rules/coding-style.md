# Coding Style & Standards

When writing code in this project (Node.js/ESM), adhere to the following:

## 1. Syntax & Structure
- **ES Modules**: Use `import` / `export`, avoiding CommonJS `require`.
- **Async/Await**: Use `async/await` over raw Promises.
- **Error Handling**: Wrap external API calls (Gemini, R2) in `try-catch` blocks. Implement retry logic for network requests.

## 2. Documentation
- **JSDoc**: Add JSDoc comments to all major classes and methods.
- **Comments**: Explain 'WHY', not just 'WHAT'.

## 3. Logs & UX
- **User Feedback**: Use emojis in `console.log` for key milestones (e.g., 🎙️, 💾).
- **Progress**: Use `cli-progress` for long-running tasks.

## 4. Configuration
- **Env Vars**: Never hardcode secrets. Use `process.env` and validate existence.

