BASAM Chess Review — Python + Stockfish for Render

WHAT THIS VERSION DOES
- Keeps the original chessboard CSS and Neo piece display from FIX1.
- Uses a Python Flask backend to fetch public Chess.com archives and games.
- Runs Stockfish on the Render server using python-chess (not in the browser).
- Uses background analysis jobs so the browser can poll progress.

RENDER DEPLOY (Docker)
1) Upload this project to a GitHub repository.
2) In Render choose New + > Web Service and connect that repository.
3) Choose Docker runtime (Render should detect the Dockerfile).
4) Set plan to Free, then deploy.
5) After deploy, open /health. It should return status=ok and engine_found=true.
6) Open the home page, enter a Chess.com username, choose a game, and press Start Analysis.

If setting commands manually:
- Runtime: Docker
- Dockerfile path: ./Dockerfile
- Docker context: .

NOTES
- Render Free services sleep after 15 minutes without traffic and may take about a minute to wake.
- Free service files are ephemeral; this app keeps analysis jobs in memory and does not promise to retain results after a restart.
- Chess.com PubAPI provides public data only. No Chess.com password is required.
- Analysis is limited to 200 half-moves and uses a modest time/depth suitable for a free instance.
