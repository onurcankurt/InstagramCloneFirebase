# Uncomment the next line to define a global platform for your project
# platform :ios, '16.4'

target 'InstaCloneFirebase' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

pod 'FirebaseAnalytics'
pod 'FirebaseAuth'
pod 'FirebaseFirestore'
pod 'FirebaseCore'
pod 'FirebaseStorage'
pod 'SDWebImage'

  # Pods for InstaCloneFirebase
  
  post_install do |installer|
      xcode_base_version = `xcodebuild -version | grep 'Xcode' | awk '{print $2}' | cut -d . -f 1`

      installer.pods_project.targets.each do |target|
          target.build_configurations.each do |config|
              # For xcode 15+ only
               if config.base_configuration_reference && Integer(xcode_base_version) >= 15
                  xcconfig_path = config.base_configuration_reference.real_path
                  xcconfig = File.read(xcconfig_path)
                  xcconfig_mod = xcconfig.gsub(/DT_TOOLCHAIN_DIR/, "TOOLCHAIN_DIR")
                  File.open(xcconfig_path, "w") { |file| file << xcconfig_mod }
              end
          end
      end
  end

end
