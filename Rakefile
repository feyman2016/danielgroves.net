task default: %w[build]

task :version do
  jekyll "--version"
end

task :watch do
  jekyll "--watch --future"
end

task :build => :version do
  clean
  jekyll "build"
end

task :build_all => :version do
  clean
  jekyll "build --future --drafts"
end

task :deploy => :build do
  branches = `git branch`

  if branches.include? "* master"
    puts "On master branch, will attempt to deploy"
    system "rsync -avz --delete _site/ danielsgroves@danielgroves.net:temp/"
  else
    puts "Cannot deploy non-master branch"
  end
end

def jekyll(args)
  system "jekyll #{args}"
end

def clean
  system "rm -Rf _site/"
end
