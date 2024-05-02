If you `devenv up` and then CTRL+C to quit, redis exits cleanly.

If you `devenv test`, once the tests are done redis is still running and has to be killed.

devenv test output (aarch64 darwin):

```
• Overriding .devenv to .devenv.kTAG5GNccM7u
• Building tests ...
• Using Cachix: devenv
✔ Building tests in 2.8s.
• Building processes ...
✔ Building processes in 2.6s.
• Starting processes ...
• Building shell ...
✔ Building shell in 2.2s.
• PID is 31959
• Stop:      $ devenv processes stop
✔ Starting processes in 2.2s.
• Running tests ...
• Building shell ...
✔ Building shell in 1.3s.
evaluating derivation 'flake:nixpkgs#bashInteractive'hello from devenv
git version 2.44.0
{"level":"warn","error":"open /Users/bdimchef/.config/process-compose/settings.yaml: no such file or directory","time":"2024-05-02T09:22:35-04:00","message":"Error reading settings file /Users/bdimchef/.config/process-compose/settings.yaml"}
[redis	] 32106:C 02 May 2024 09:22:35.678 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
[redis	] 32106:C 02 May 2024 09:22:35.678 * Redis version=7.2.4, bits=64, commit=00000000, modified=0, pid=32106, just started
[redis	] 32106:C 02 May 2024 09:22:35.678 * Configuration loaded
[redis	] 32106:M 02 May 2024 09:22:35.678 * Increased maximum number of open files to 10032 (it was originally set to 256).
[redis	] 32106:M 02 May 2024 09:22:35.678 * monotonic clock: POSIX clock_gettime
[redis	] 32106:M 02 May 2024 09:22:35.679 * Running mode=standalone, port=6379.
[redis	] 32106:M 02 May 2024 09:22:35.679 # WARNING: The TCP backlog setting of 511 cannot be enforced because kern.ipc.somaxconn is set to the lower value of 128.
[redis	] 32106:M 02 May 2024 09:22:35.679 * Server initialized
[redis	] 32106:M 02 May 2024 09:22:35.680 * Ready to accept connections tcp
hello from devenv
git version 2.44.0
• Setting up shell environment ...
hello from devenv
git version 2.44.0
• Testing ...
Running tests
✔ Running tests in 3.2s.
• Stopping process with PID 31959
Stopping processes...
• Tests passed :)
[redis	] 32106:signal-handler (1714656156) Received SIGTERM scheduling shutdown...
Processes stopped.
```

still running, and i gotta `kill -9`:

```
❯ pgrep redis-server
32106
❯ pkill redis-server
❯ pgrep redis-server
32106
❯ pkill -2 redis-server
❯ pgrep redis-server
32106
❯ pkill -9 redis-server
❯ pgrep redis-server
```
