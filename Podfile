# Uncomment the next line to define a global platform for your project
 platform :ios, '15.6'

target 'VideoIdSDK2Sample' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for VideoIdSDK2Sample
    pod 'IDentityVideoIdSDK2.0'
    pod 'IDentityVideoIdModels'
    pod 'TensorFlowLiteSwift', '~> 2.7.0'
    pod 'GoogleMLKit/TextRecognition'
    pod 'GoogleMLKit/FaceDetection'
    pod 'GoogleMLKit/ImageLabeling'
    pod 'GZIP'
    pod 'OpenSSL-Universal', :git => 'https://github.com/krzyzanowskim/OpenSSL.git', :tag => '1.1.2301'  # for NFCPassportReader 1.1.9
end

post_install do |installer|
    installer.aggregate_targets.each do |aggregate_target|
        if aggregate_target.name == 'Pods-VideoIdSDK2Sample'
            aggregate_target.xcconfigs.each do |config_name, config_file|
                aggregate_target.pod_targets.each do |pod_target|
                    pod_target.specs.each do |spec|
                        if spec.attributes_hash['vendored_frameworks'] != nil or (spec.attributes_hash['ios'] != nil and spec.attributes_hash['ios']['vendored_frameworks'] != nil)
                            puts "Removing #{spec.name}"
                            config_file.frameworks.delete(spec.name)
                        end
                    end
                end
                xcconfig_path = aggregate_target.xcconfig_path(config_name)
                config_file.save_as(xcconfig_path)
            end
        end
    end
end

# install! 'cocoapods',
#   :git => {
#     :shallow_clone => false
#   }

# platform :ios, '12.0'
# use_frameworks!

# target 'YourAppTargetName' do
#   # Example of your private pod
# pod 'VideoIdIDentitySDK2.0', :git => 'https://gitlab.idmission.com/apps/sdk2.0/ios/cocoapods/identityvideoidsdk2.0.git', :tag => '10.1.16.2.2'
# pod 'VideoIdIDentityModels', :git => 'https://gitlab.idmission.com/apps/sdk2.0/ios/cocoapods/identityvideoidsdk2.0.git', :tag => '10.1.16.2.2'
# end