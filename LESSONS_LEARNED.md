# Lessons Learned - Digitwin Deployment

## What Went Wrong

1. Initial Space upload was too broad.
The first upload accidentally included many unrelated notebooks and community files, making the repo noisy and less professional.

2. Build failed with limited diagnostics.
The Space showed a generic build failure (`exit code: 6`) with very little log detail, which made root-cause identification slower.

3. Dependency scope was larger than needed.
`requirements.txt` included packages not required by the running app, increasing risk of resolver/build issues.

4. Startup reliability assumptions were implicit.
Relying on defaults for runtime behavior can make deployments less predictable across environments.

## What We Changed

1. Reduced repository scope to app essentials only.
Final deployable set:
- `app.py`
- `requirements.txt`
- `README.md`
- `me/summary.txt`
- `me/linkedin.pdf`

2. Simplified dependencies to only what is used.
Kept runtime requirements minimal and removed direct Gradio pinning to avoid SDK conflicts on Spaces.

3. Hardened app startup behavior for hosted runtime.
- Explicit host/port binding for Gradio.
- Path handling made more robust for packaged files.

4. Updated persona branding.
Changed persona name from `Ed Donner` to `Varun Sai` for personal ownership.

5. Verified deployment with runtime endpoint checks.
Confirmed app availability through Space URL and Gradio `/config` endpoint.

## Operational Best Practices Going Forward

1. Keep deployment repos single-purpose and minimal.
2. Pin key framework versions for reproducibility.
3. Keep secrets in platform secret managers only.
4. Validate startup path and environment assumptions before deployment.
5. After each deploy, verify app health immediately using URL and logs.
6. Use `uv` locally, but expect `pip` in hosted builds.
Hugging Face Spaces installs from `requirements.txt` with `pip` internally. Local development can still use `uv` (`uv sync`, `uv run`) while deployment remains `requirements.txt`-driven.

## Interview-Ready Narrative

- Problem: deployment instability and noisy repository scope.
- Approach: reduced system complexity, tightened dependency/runtime config, and validated production behavior.
- Result: stable public Space deployment with a clean, professional, shareable project footprint.

