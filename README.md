# comp-25
Comp materials with submodules to each independent team module. Please use test-25 before pulling for comp. 
This setup is meant to allow indiviudal teams to work within their own repo (existing) without damaging the code of other teams. Then updates for all teams can be pulled at once in this parent folder for comp. Note that this parent won't update automatically when changes are pushed to the submodules. Instructions for how to pull the changes here below. 
# Pulling This Repo + Working with Submodules 
## Cloning the Parent Repository with Submodules
If you are cloning the parent repository for the first time, make sure to also initialize and update the submodules:
```sh
git clone --recurse-submodules https://github.com/your-username/your-parent-repo.git
```
If you already cloned the parent repo but forgot to initialize submodules, run:
```sh
git submodule update --init --recursive
```

## Adding a New Submodule
To add a new submodule to the parent repository:
```sh
git submodule add https://github.com/user/child-repo.git path/to/submodule
```
Commit and push the changes:
```sh
git add .gitmodules path/to/submodule
git commit -m "Added new submodule"
git push origin main
```

## Updating Submodules
To pull the latest changes from all submodules:
```sh
git submodule update --remote --recursive
```

If you want to update a specific submodule:
```sh
cd path/to/submodule
git pull origin main
cd ..
git add path/to/submodule
git commit -m "Updated submodule reference"
git push origin main
```

## Making Changes to a Submodule
1. Navigate into the submodule directory:
   ```sh
   cd path/to/submodule
   ```
2. Make changes, then commit and push them to the submodule's repository:
   ```sh
   git add .
   git commit -m "Updated submodule code"
   git push origin main
   ```
3. Go back to the parent repository and update the submodule reference:
   ```sh
   cd ..
   git add path/to/submodule
   git commit -m "Updated submodule reference"
   git push origin main
   ```

## Switching Submodule to a Specific Branch
If you need a submodule to follow a specific branch, configure it:
```sh
git config -f .gitmodules submodule.path/to/submodule.branch dev
git add .gitmodules
git commit -m "Set submodule to track 'dev' branch"
```

## Removing a Submodule
If you no longer need a submodule, remove it with:
```sh
git submodule deinit -f path/to/submodule
rm -rf path/to/submodule
rm -rf .git/modules/path/to/submodule
git rm -f path/to/submodule
git commit -m "Removed submodule"
git push origin main
```

## Summary of Common Commands
| Action | Command |
|--------|---------|
| Clone parent repo with submodules | `git clone --recurse-submodules <repo>` |
| Initialize and update submodules | `git submodule update --init --recursive` |
| Add a new submodule | `git submodule add <url> <path>` |
| Update all submodules | `git submodule update --remote --recursive` |
| Update a specific submodule | `cd <submodule> && git pull origin main` |
| Remove a submodule | `git submodule deinit -f <path>` and `git rm -f <path>` |


