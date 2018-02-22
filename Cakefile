# This is a sample Cakefile for common iOS project
# Language : Swift
# Credit : Duy Nguyen - http://duynb.com
# References :
# https://github.com/jcampbell05/xcake
# https://github.com/jcampbell05/xcake/blob/master/docs/Cakefile.md

#======= GLOBAL VARIABLES =======
# Some global variables to use these values in a consistent way across whole file

projectName = "YOURPROJECTNAME"
companyIdentifier = "com.yourcompanyname"
organization = "Duy Nguyen"
# for Beesightsoft use
# companyIdentifier = "com.beesightsoft.testing"
# organization = "Beesightsoft"
iOSdeploymentTarget = "10.0"
currentSwiftVersion = "3.2" # to set "Use Legacy Swift ..." to "No"

#======= GLOBAL VARIABLES =======

#======= NOT USE FOR NOW =======
#=== 3d-party integration keys (global variables)

# The values below will be used to set "user-defined" build settings
# for build configurations on target level,
# so we can reuse the same, lets say, "test" FB key
# within several "test" configurations (for example, the same test key
# would be used for "Debug" and "Staging" configurations), and can easily
# see what is the value/key we use for testing and production,
# and even update it in future if needed.

# "FACEBOOK_KEY"

#facebookProdKey = "888888888888888"
#facebookTestKey = "999999999999999"

#===
#======= NOT USE FOR NOW =======

# High level project settings

project.name = projectName.downcase
project.organization = organization

#===

# Below we explicitly define the list of project build configurations.
# If you do not define it explicitly, Xcake will implicitly define default ones,
# that are equivalent to this:
#
# project.debug_configuration :Debug
# project.release_configuration :Release
#

project.debug_configuration :Debug # for local development/debugging only
project.release_configuration :Release
project.debug_configuration :integration # for internal development/debugging only
project.release_configuration :staging # for alpha and beta AdHoc builds
project.release_configuration :production # for App Store ready AdHoc builds

# Note, that Xcake will also automatically create set of project "Schemes" -
# one for each build configuration, their names will be constructed from 
# project name and configuration name, separated by dash, like this:
#
# "<project_name>-<configuration_name>"
#
# NOTE: every scheme will have the same build configuration
# for all phases (Run, Test, Profile, Archive). If you need different build configurations
# based on phase - lets say one configuration for Run, but different one for Archive -
# consider to have different build configurations (and as result - build shemes) for these purposes
# (as proposed in this sample file).
#
# For this example, schemes will be:
#
# "YOURPROJECTNAME-integration"
# "YOURPROJECTNAME-staging"
# "YOURPROJECTNAME-production"

#=== DEFAULT target settings

# Below we define "project level" build configurations.
# REMEMBER this entiire file is just an interpretable script,
# and the structure below is just a loop.
# At every iteration we have reference to one
# of the build configurations defined above explicitly or implicitly.

# In this case, we set the same build settings to each configuration,
# but, if we need to have some settings to be different for different
# configurations, then you can use "if" expression to set different build settings
# dependiong on "configuration.name" (we will see example of that in target settings below in this document).

# NOTE : MOSTLY WE DO NOT NEED TO MODIFY BELOW CONFIGUATIONS

project.all_configurations.each do |configuration|

    # the settings listed below are just a copy
    # of what Xcode sets explicitly in a newly created Xcode
    # project file in comparison with default values
    # (the values that are marked with bold font).

    configuration.settings["ENABLE_BITCODE"] = "YES"

    configuration.settings["SDKROOT"] = "iphoneos"
    configuration.settings["GCC_DYNAMIC_NO_PIC"] = "NO"
    configuration.settings["OTHER_CFLAGS"] = "$(inherited) -DNS_BLOCK_ASSERTIONS=1"
    configuration.settings["GCC_C_LANGUAGE_STANDARD"] = "gnu99"
    configuration.settings["CLANG_ENABLE_MODULES"] = "YES"
    configuration.settings["CLANG_ENABLE_OBJC_ARC"] = "YES"
    configuration.settings["ENABLE_NS_ASSERTIONS"] = "NO"
    configuration.settings["ENABLE_STRICT_OBJC_MSGSEND"] = "YES"
    configuration.settings["CLANG_WARN_EMPTY_BODY"] = "YES"
    configuration.settings["CLANG_WARN_BOOL_CONVERSION"] = "YES"
    configuration.settings["CLANG_WARN_CONSTANT_CONVERSION"] = "YES"
    configuration.settings["GCC_WARN_64_TO_32_BIT_CONVERSION"] = "YES"
    configuration.settings["CLANG_WARN_INT_CONVERSION"] = "YES"
    configuration.settings["GCC_WARN_ABOUT_RETURN_TYPE"] = "YES_ERROR"
    configuration.settings["GCC_WARN_UNINITIALIZED_AUTOS"] = "YES_AGGRESSIVE"
    configuration.settings["CLANG_WARN_UNREACHABLE_CODE"] = "YES"
    configuration.settings["GCC_WARN_UNUSED_FUNCTION"] = "YES"
    configuration.settings["GCC_WARN_UNUSED_VARIABLE"] = "YES"
    configuration.settings["CLANG_WARN_DIRECT_OBJC_ISA_USAGE"] = "YES_ERROR"
    configuration.settings["CLANG_WARN__DUPLICATE_METHOD_MATCH"] = "YES"
    configuration.settings["GCC_WARN_UNDECLARED_SELECTOR"] = "YES"
    configuration.settings["CLANG_WARN_OBJC_ROOT_CLASS"] = "YES_ERROR"

    configuration.settings["CURRENT_PROJECT_VERSION"] = "1" # just default non-empty value

    configuration.settings["DEFINES_MODULE"] = "YES" # http://stackoverflow.com/a/27251979

    configuration.settings["SWIFT_OPTIMIZATION_LEVEL"] = "-Onone"

    configuration.settings["CLANG_WARN_INFINITE_RECURSION"] = "YES" # Xcode 8
    configuration.settings["CLANG_WARN_SUSPICIOUS_MOVE"] = "YES" # Xcode 8
    configuration.settings["ENABLE_STRICT_OBJC_MSGSEND"] = "YES" # Xcode 8
    configuration.settings["GCC_NO_COMMON_BLOCKS"] = "YES"
    configuration.settings["ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES"] = "$(inherited)" # "YES"

    configuration.settings["SWIFT_VERSION"] = currentSwiftVersion

    #===

    if configuration.name == "production"

        configuration.settings["DEBUG_INFORMATION_FORMAT"] = "dwarf-with-dsym"
        configuration.settings["SWIFT_OPTIMIZATION_LEVEL"] = "-Owholemodule" # Xcode 8

    end
end

#=== Targets

# So far, we've defined poject settings and
# project level build configuration settings
# (which define defaults for target level build configurations).
#
# Now it's time to define target-level build settings.

# Below we define "application"-type target and
# put all it's settings (including definition or related unit test targets)
# inside "application_for ... do ... end" structure.

target do |target|

    target.name = project.name
    target.language = :swift
    target.type = :application
    target.platform = :ios
    target.deployment_target = iOSdeploymentTarget

    #===

    # Now lets set target-level build settigns.
    # Again, the structure below is just a loop,
    # everything between "target.all_configurations.each do |configuration|"
    # and corresponding "end" (see below on the same level in the very bottom of the file)
    # is body of this loop, that repeats every iteration. This loop goes through
    # the list of build configurations (defined above) and on each iteration
    # we have variable "configuration" that contains reference to one
    # of the build configurations in CONTEXT of the TARGET. This is equivalent of setting
    # build settings on target-level in Xcode (you can access it if you choose to
    # see build settigns by "Levels", not "Combined").

    #=== Build Settings - Debug & Release

    target.all_configurations.each do |configuration|

        configuration.product_bundle_identifier = companyIdentifier + "." + project.name.downcase + "." + configuration.name
        configuration.supported_devices = :iphone_only
        configuration.settings["INFOPLIST_FILE"] = "Info/" + "Info.plist"
        configuration.settings["PRODUCT_NAME"] = project.name.downcase + "-" + configuration.name
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["FRAMEWORK_SEARCH_PATHS"] = "$(inherited)"
        configuration.settings["OTHER_LDFLAGS"] = "$(inherited) -ObjC"
        # make configuration name available in run time:
        configuration.settings["GCC_PREPROCESSOR_DEFINITIONS"] = "$(inherited) " + configuration.name.upcase + "=1" # Obj-C support
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["SWIFT_VERSION"] = currentSwiftVersion
        
    end

    #=== Build Settings - Per-user-configuration
    # NOTE: any configuration-specific settings below will override
    # common settings that you already applied above inside this
    # "target.all_configurations.each do |configuration|" block

    target.debug_configuration :integration do |configuration|
        configuration.product_bundle_identifier = companyIdentifier + "." + project.name.downcase + "." + configuration.name
        configuration.supported_devices = :iphone_only
        configuration.settings["INFOPLIST_FILE"] = "Info/" + "Info-" + configuration.name + ".plist"
        configuration.settings["PRODUCT_NAME"] = project.name.downcase + "-" + configuration.name
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["FRAMEWORK_SEARCH_PATHS"] = "$(inherited)"
        configuration.settings["OTHER_LDFLAGS"] = "$(inherited) -ObjC"
        # make configuration name available in run time:
        configuration.settings["GCC_PREPROCESSOR_DEFINITIONS"] = "$(inherited) " + configuration.name.upcase + "=1" # Obj-C support
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["SWIFT_VERSION"] = currentSwiftVersion
    end

    target.release_configuration :staging do |configuration|
        configuration.product_bundle_identifier = companyIdentifier + "." + project.name.downcase + "." + configuration.name
        configuration.supported_devices = :iphone_only
        configuration.settings["INFOPLIST_FILE"] = "Info/" + "Info-" + configuration.name + ".plist"
        configuration.settings["PRODUCT_NAME"] = project.name.downcase + "-" + configuration.name
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["FRAMEWORK_SEARCH_PATHS"] = "$(inherited)"
        configuration.settings["OTHER_LDFLAGS"] = "$(inherited) -ObjC"
        # make configuration name available in run time:
        configuration.settings["GCC_PREPROCESSOR_DEFINITIONS"] = "$(inherited) " + configuration.name.upcase + "=1" # Obj-C support
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["SWIFT_VERSION"] = currentSwiftVersion
    end
    
    target.release_configuration :production do |configuration|
        configuration.product_bundle_identifier = companyIdentifier + "." + project.name.downcase + "." + configuration.name
        configuration.supported_devices = :iphone_only
        configuration.settings["INFOPLIST_FILE"] = "Info/" + "Info-" + configuration.name + ".plist"
        configuration.settings["PRODUCT_NAME"] = project.name.downcase + "-" + configuration.name
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["FRAMEWORK_SEARCH_PATHS"] = "$(inherited)"
        configuration.settings["OTHER_LDFLAGS"] = "$(inherited) -ObjC"
        # make configuration name available in run time:
        configuration.settings["GCC_PREPROCESSOR_DEFINITIONS"] = "$(inherited) " + configuration.name.upcase + "=1" # Obj-C support
        configuration.settings["OTHER_SWIFT_FLAGS"] = "$(inherited) -D" + configuration.name.upcase # Swift support
        configuration.settings["SWIFT_VERSION"] = currentSwiftVersion
    end

    #======= NOT USE FOR NOW =======
    #=== Extra System Frameworks

    # Here is how we tell Xcake to include Apple system framework
    # into the target.

    # NOTE: "target.system_frameworks" is an array, that always have at least
    # "Foundation" and "UIKit", os it's always non-empty and we should not initialize it
    # before adding something there, so we jsut add values, one at a time (one per each line below).

    #target.system_frameworks << "AdSupport"
    #target.system_frameworks << "QuartzCore"

    #======= NOT USE FOR NOW =======

    #=== Source Files

    # Here is how we tell Xcake where to look for source files
    # which need to be added into the target. Moreover, the folder struture
    # will be re-created with Xcode groups.

    # NOTE: "target.include_files" is an array, that is empty by default
    # (no source files will be added to the target). So it's our responsibility
    # to initialize this array (with "=" operand) before adding values/elements
    # into it (with "<<" operand). Remember, this file is a Ruby script, and
    # that's just how Ruby works.

    target.include_files = ["Resources/**/*.*"] # initialize array with 1 element
    target.include_files << "Helpers/**/*.*"  # add value into already non-empty array
    target.include_files << "Libs/**/*.*"  # add value into already non-empty array
    target.include_files << "Infrastructures/**/*.*"  # add another value
    target.include_files << "Models/**/*.*"  # add another value
    target.include_files << "Views/**/*.*"  # add another value
    target.include_files << "Info/**/*.*"  # add another value
    target.include_files << "Base.lproj/**/*.*"  # add another value
    target.include_files << "AppDelegate.swift"  # add another value
    target.include_files << "Assets.xcassets"  # add another value
    
end
