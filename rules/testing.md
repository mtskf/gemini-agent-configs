# Testing Rules & Strategy

## ⛔ CRITICAL: NO LIVE API CALLS
**Strictly forbidden to call real external APIs during automated tests.**
Tests must run offline, cost nothing, and be deterministic.

---

## 1. Mocking Requirements

### Gemini (Content Processor)
- **Rule**: NEVER call Google Generative AI API in tests.
- **Action**: Mock `GoogleGenerativeAI` client or the `generateContent` method.
- **Response**: Return a fixed, valid JSON structure (matching `SPEC.md` schema).

### Gemini TTS (Audio Synthesizer)
- **Rule**: **ABSOLUTE PROHIBITION** on calling TTS API (Cost Risk).
- **Action**: Mock the synthesizer module to return a dummy `Buffer` (e.g., empty or 1-second silence).
- **Verification**: Ensure tests fail immediately if an actual network request is attempted.

### Cloudflare R2 (Storage)
- **Rule**: No S3/R2 uploads.
- **Action**: Mock `@aws-sdk/client-s3`.
- **Response**: Return success immediately for `PutObjectCommand`.

## 2. Test Coverage

- **Unit Tests**: Focus on logic within `Fetcher`, `Processor` (parsing logic), `Synthesizer` (chunking logic), and `RSS Builder`.
- **Integration Tests**: Verify the `WorkflowController` pipeline connects these mocked modules correctly.

## 3. Environment

- **Vars**: Tests should inject their own sanitized `process.env` (e.g., `GEMINI_API_KEY=mock_key`).
- **Setup**: Use `jest.setup.js` or `beforeAll` to enforce global mocks if necessary.
