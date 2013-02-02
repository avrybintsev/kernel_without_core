gitgit clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git 

kernel_without_core

git clone --no-hardlinks kernel_without_core kernel_core



cd kernel_without_core

git filter-branch --subdirectory-filter net/ HEAD

git filter-branch -f --tree-filter 'rm -rf core/' HEAD

git remote rm origin

git remote add origin git@github.com:avrybintsev/kernel_without_core.git

git push origin master



cd ../kernel_core

git filter-branch --subdirectory-filter /net/core HEAD

git remote rm origin

git remote add origin git@github.com:avrybintsev/kernel_core.git

git push origin master
