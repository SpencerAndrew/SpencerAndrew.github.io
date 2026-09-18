# SpencerAndrew.github.io
Spencer Andrew's Professional Portfolio

Root causes:
• Both AI forms collect visitor-provided Gemini keys but omit them from API calls.
• The client assumes an old Gemini model exists, masks errors, and delays rendering submitted chat text.
• Mobile navigation keeps a stale icon reference after Lucide replaces its node.
• Volunteer rendering has no target container.
• Unclosed analytics and volunteer wrappers and a duplicate cover-letter wrapper corrupt section/modal nesting.
• News cards with missing video IDs request invalid empty YouTube embeds.

Changes:
• Preserve visitor-supplied-key behavior, portfolio content, and existing styling. Pass each form's key in the request header rather than URLs or storage; discover an available stable Flash model; bound requests with a timeout; retry only transient HTTP failures; and show actionable errors. Render chat text literally and immediately. Restore markup, volunteer cards, current-icon lookup, menu accessibility state, and Escape handling. Keep news cards but show an unavailable message until a video ID exists.
• Add dependency-free Node regression tests and require validation before default-branch Pages publication. Test Pages packaging on repair branches without deploying, and publish only index.html (not test files).

Verification: 
• All 15 targeted checks plus Pages packaging passed for latest repair commit 21dfe292.
• Coverage includes inline JavaScript parsing, DOM lookup/navigation targets, full initialization, resume switching, experience filtering, volunteer rendering, news video fallbacks, markup structure, both AI form success/failure flows, model discovery, missing keys, permanent API errors, blocked responses, immediate literal chat rendering, and repeated icon replacement.
• Tests use lightweight DOM simulation and mocked Google responses. Live Gemini generation, real-browser console/network checks, and responsive visual testing remain outstanding. No real credentials are used in tests; visitors still supply their own Gemini key.

Deployment status:
• Not merged or deployed. The user authorizes deployment, but GitLab rejected the merge quick action with HTTP 403: merge quick actions cannot be used with AI workflows. A human must merge this MR. The main-branch pipeline then reruns validation and automatically publishes Pages only if validation succeeds. No bypass was attempted.
