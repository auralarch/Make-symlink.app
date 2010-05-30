require 'rake/clean'

APP = "Make-symlink.app"

def package_dir
  "build/package"
end
def package_app_dir
  "#{package_dir}/#{APP}"
end
def dmg_file
  "build/#{APP}.dmg"
end
def bluecloth?
  @bluecloth ||= begin
				   %w[rubygems bluecloth].each {|l| require l }
				   @bluecloth = true
				 rescue GEM::LoadError
				   @bluecloth = false
				 end
end

CLEAN.include("build/*.html", package_dir)
CLOBBER.include("build")

desc "Build package dmg (disk image)."
task :default => "build"

file "build" => FileList[dmg_file]

file dmg_file => FileList["Rakefile", "README.markdown", "Icon*", "Contents/**/*"] do |t|
  Rake::Task[package_dir].invoke
  sh %Q[hdiutil create -ov -srcfolder #{package_dir} -format UDBZ -volname "#{APP}" #{dmg_file}]
  puts "Find your dmg at build/#{APP}.dmg"
end

file package_dir => FileList[package_app_dir, "#{package_dir}/README.rtf"]

file package_app_dir do
  mkdir_p package_app_dir
  cp_r FileList["Icon*", "Contents"], package_app_dir
end

file "#{package_dir}/README.rtf" => FileList["README.markdown", "build/README.html"] do |t|
  rm t.name if File.exist?(t.name)
  sh "textutil -convert rtf -output #{t.name} build/README.html"
end

file "build/README.html" => FileList["README.markdown"] do |t|
  rm t.name if File.exist?(t.name)
  if bluecloth?
	doc = BlueCloth.new(File.read(FileList["README.markdown"].first))
	File.open(t.name, 'w') do |f|
	  f.puts(doc.to_html)
	end
  else
	puts "I can't find the bluecloth gem, so, rather than just complaining, I'm just using README.markdown"
	cp "README.markdown", package_dir
  end
end
