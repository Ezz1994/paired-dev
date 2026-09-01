## Agent workflow

For multi-file features, or changes larger than roughly 50 lines:
implement via the `paired-dev:developer` agent, then pass the changed
files and a summary to the `paired-dev:reviewer` agent and address its
findings before reporting the work complete.

Skip this for typos, one-liners, config tweaks, and any change already
being discussed in the current session.
