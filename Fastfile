default_platform(:ios)

APP_NAME = "Tower App.xcworkspace"
STAGING_SCHEME = "Taste N Go Dev"
PRODUCTION_SCHEME = "Taste N Go"

def update_build_number(build_number: nil)
  # If build number is provided explicitly, then use that build number instead
  if build_number  
    increment_build_number(
      build_number: build_number
    )
  # Otherwise, increment build number based from previous build number
  else
    increment_build_number
  end
end

def update_version_number(bump_type)
  # Update version number if bump_type has been provided
  if bump_type
    increment_version_number(bump_type: bump_type)
  end
end

def build_app(scheme, bump_type = nil)
  # If bump_type has been provided then reset the build number to 1
  if bump_type 
    update_version_number(bump_type)
    update_build_number(build_number: "1")
  else
    update_build_number()
  end
  build_app(workspace: APP_NAME, scheme: scheme)
  #upload_to_app_store(skip_metadata: true, skip_screenshots: true)
end

platform :ios do
  desc "Push a new production build to the App Store"
  lane :production do |options|
    bump_type = options[:bump_type]
    build_app(scheme = STAGING_SCHEME, bump_type = bump_type)
  end

  desc "Upload new staging build to the App Store"
  lane :staging do |options|
    bump_type = options[:bump_type]
    build_app(scheme = PRODUCTION_SCHEME, bump_type = bump_type)
  end
end

