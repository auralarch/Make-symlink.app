APP = "Make-symlink.app"

file "build" => FileList["Icon*", "Rakefile", "Contents/**/*"] do
  require 'fileutils'
  package_dir = "build/package/#{APP}"
  FileUtils.mkdir_p package_dir
  FileUtils.cp_r [Dir["Icon*"], "Contents"].flatten, package_dir
  FileUtils.cp Dir["README*"], "build/package"
  sh %Q[hdiutil create -ov -srcfolder #{package_dir} -format UDBZ -volname "#{APP}" "build/#{APP}.dmg"]
  FileUtils.rm_r "build/package"
  puts "Find your dmg at build/#{APP}.dmg"
end

desc "Build package dmg"
task :default => "build"
