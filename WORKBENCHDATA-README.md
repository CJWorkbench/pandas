To add a new feature:

1. Submit a pull request to the Pandas project
1. Get it accepted into `master` (here called `upstream/master`)
1. `git fetch upstream && git merge upstream/master` (We track master. Our
   only local edit is the change of package name, `workbenchdata-pandas`
   instead of `pandas`.)
1. `git tag v0.24.0aXXX`, where XXX is the number we want to release.
1. `git push v0.24.0aXXX`
1. `python3 setup.py sdist`
1. `pip3 install --user cibuildwheel && CIBW_SKIP='cp2* cp*i686* cp34* cp35*' cibuildwheel --output-dir wheelhouse`
1. `twine upload dist/* wheelhouse/*` (Create a username at https://pypi.org
   and then email `adam@adamhooper.com` to be added to the maintainer list.)

Now update the dependent project to depend on `workbenchdata-pandas==0.24.0aX`
