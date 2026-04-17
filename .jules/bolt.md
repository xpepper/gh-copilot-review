## 2024-05-17 - Bash Subprocess Overhead
**Learning:** Spawning subprocesses (`sed`, `grep`, subshells with pipelines) in bash scripts has massive performance overhead compared to native shell string manipulation and regex. What takes ~4s for 1000 iterations via `sed` takes only ~0.03s natively.
**Action:** Always favor native bash parameter expansion (e.g. `${var#prefix}`) and regex matching (`[[ "$var" =~ regex ]]`) over pipes to external text parsing tools for critical paths.
