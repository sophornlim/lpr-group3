POS Backend

How to run

1. Install dependencies:

   npm install

2. Start development server (will free port 5000 first):

   npm run dev

3. Start on an alternate port (5001):

   npm run dev:alt

Troubleshooting

- Error: "Port 5000 is already in use"
  - The project includes a `predev` script that runs `npx kill-port 5000` before starting. This will attempt to free the port automatically.
  - Alternatively, run `npx kill-port 5000` manually or find the PID and stop it:

    # PowerShell
    Get-NetTCPConnection -LocalPort 5000 | Select-Object LocalAddress,LocalPort,State,OwningProcess
    Stop-Process -Id <PID> -Force

- If a non-Node process holds the port (docker, etc.), stop that service instead.

Notes

- The server reads the `PORT` environment variable; set it to change ports.
- `dev:alt` uses `cross-env` to set `PORT=5001` cross-platform.
