# NeiroPay

An OAuth-authenticated remote MCP connector for Solana tipping to X accounts.

MCP URL: https://tip.neiropay.app/mcp

Install this plugin through the Grok Bot/Cursor plugin dashboard, then Authenticate. Sign in to NeiroPay with X and approve the displayed application for your account. Authentication belongs to each user. OAuth credentials must remain on the host's protected connector backend, not in agent-readable files.

Tools: account, search_tokens, prepare_tip, send_tip, tip_status, received_tips, incoming_tips.

Incoming tips are confirmed NeiroPay payments to the authenticated account. `received_tips` provides paginated history; `incoming_tips` provides a resumable polling cursor. A Grok host routine must schedule checks and notifications; connecting alone does not create a notification subscription.

The backend binds the paying account, checks existing eligibility and fees, handles CDP signing and prevents duplicate sends. Token search uses exact Solana mints and requires selection when ambiguous. Disconnect at https://tip.neiropay.app/connect/grok.

The plugin contains no secrets and needs no local command, script or API key. OAuth uses authorization code + S256 PKCE and the tips:execute scope. No key export or arbitrary-address withdrawal tools are exposed. An authorized bot can invoke send_tip; protected token storage does not itself prove human intent for every request.

This package is prepared for installation/review. Marketplace approval and actual Grok Bot installation must be verified separately; publication is not implied by the files in this directory.
