# Infra team demo 

We like git, everyone likes git, we got gitlab

- We're talking about svn -> gitlab migration as a department (today in fact)
- Some teams including us are using gitlab already, if they have few deps. on current infra.

## Here's what you can do 

- Gitlab is auth via google, possible sync. via ldap via api 
    - i have a script, i need to progress this - anyone wanna help?
- We own top-level Mintel group
- We create sub-teams, different members in different teams with different permissions
- Repo's are called Projects 
- We created an Infra group - I invited you all


## new project

- create a project
    - `git push --set-upstream git@gitlab.com:mintel/infra/a-test-project2.git master`

- add a readme
- git clone it 
- local commit
    - nothing remote
- push 
    - remote updates

## branch

- local and update readme
- push to remote 
    - `git push -u origin readme-update`
- origin is remote 
- readme-update is the branch
- `git branch -a` now shows remotes which you can push and pull to
- encourages forking

## create a merge request

now cleanup

`git push --delete origin readme-update`
`git remote prune origin`

## can do CI / CD
- talk about runners
## can build container images
- show images in satosh - work with docker
- show auth

## show off satoshi ci pipeline


## termins

### rebase and merging

ways to merge changes from one branch into another

Merge: A three-way merge between two latest branches (say your branch and master) and generates a new snapshot (commit)

Rebase: Basically replay your commits on your branch ontop of master
- reduces merge-commit noise
- makes history cleaner
- merges in requested branch, apply commits that i've done locally ontop of that merge
- merge conflicts more requestent
- maybe more complicated

### squash

squash multiple commits messages into a single commit message (easy of reading?)

### cherry pick

pick selected commits from one branch to another

### origin / remote 

Git is distributed, you can referencem multiple upstreams and merge between then

origin is a local alias for a particular remote repository, you can define your own

you can list them via `git remote -v`
