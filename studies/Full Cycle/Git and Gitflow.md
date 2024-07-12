status: #fleeting 
tags: #education/programing #gitflow
### gitflow

Alternative model to branches of Git then use a lot of branches from the primary branch.
The main model user branchs:
- Master
- Hotfix
- Release
- Develop (always updated with Master branch)
- Feature

#### docs
https://github.com/petervanderdoes/gitflow-avh/wiki/Installation

#### commands
```bash
# To init
git flow init

# Start a new branch
git flow feature start newbranch

# Finish the new branch
git flow feature finish  newbranch
```

