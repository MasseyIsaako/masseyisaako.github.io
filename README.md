# Deploy scripts
For deployment, I have created two separate env branches. One for stage and another for production. The deployment is very simple. We build the assets and optimise for the environments. Then we add and commit them, but we only push the dist directory to the environment branches.

The dist folder git code was found here: https://gist.github.com/joshuapekera/ef364073b01fb0e21d3f.

### Stage
`git checkout master && git branch -D env/stage && git checkout -b env/stage && npm run build && git add -f dist && git commit -m "env/stage: Deploying assets to stage." && git subtree push --prefix dist origin env/stage`

Prior to running this script, we need to delete the env/stage branch in Github. This branch is hosted on Github Pages.

### Prod:
`git merge master --no-commit && git add -A . && git commit -m "env/prod: Deploying assets to prod." && git push origin env/prod"`

We are using Netlify to handle our deployments. All we need to do is push the code up to env/prod and run the deployment pipeline in Netlify. The site automatically gets updated for us.  This branch is hosted on Netlify.