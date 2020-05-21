# Change BundleID & Name & xscheme

It changes bundleId, display name and xscheme

```shell
#!/bin/bash

#
#
# BunleIdentifier
#
#
read -p "Enter BunleIdentifier: " identifier
echo "Your select bundleIdentifier is $identifier"

cd AlbarakaApp.xcodeproj

# Get BundleIdentifier Name
var=$( awk -F '=' '/PRODUCT_BUNDLE_IDENTIFIER/ {print $2; exit}' project.pbxproj)

echo 'Current Name is' $var
# Set BundleIdentifier Name
sed -i '' "s/$var/ $identifier;/g" project.pbxproj
echo "BundleIdentifier has changed"

#
#
# DisplayName
#
#
read -p "Enter display name: " displayName
echo "Your new app name is $displayName"

# Set Product Name
sed -i '' "s/PRODUCT_NAME = [^\"]*/PRODUCT_NAME = \"$displayName\";/" 'project.pbxproj'

echo "Product Name has changed"

#
#
# Scheme
#
#
read -p "Are you sure? [Yy/Nn]" REPLY
echo    # (optional) move to a new line
if [[ $REPLY =~ ^[Yy]$ ]]
then
    echo "Xscheme is updating for ProdRelease Mode"

    cd xcshareddata/xcschemes
    # XcScheme buildConfiguration
    sed -i '' -e '/<LaunchAction/,/<\/LaunchAction/ s/buildConfiguration = "[^"]*"/buildConfiguration = "ProdRelease"/' 'AlbarakaApp.xcscheme'
    # selectedDebuggerIdentifier
    sed -i '' -e '/<LaunchAction/,/<\/LaunchAction/ s/selectedDebuggerIdentifier = "[^"]*"/selectedDebuggerIdentifier = ""/' 'AlbarakaApp.xcscheme'
    # selectedDebuggerIdentifier
    sed -i '' -e '/<LaunchAction/,/<\/LaunchAction/ s/selectedLauncherIdentifier = "[^"]*"/selectedLauncherIdentifier = "Xcode.IDEFoundation.Launcher.PosixSpawn"/' 'AlbarakaApp.xcscheme'

    # Archive
    sed -i '' -e '/<ArchiveAction/,/<\/ArchiveAction/ s/buildConfiguration = "[^"]*"/buildConfiguration = "ProdRelease"/' 'AlbarakaApp.xcscheme'

else
    echo "No production Mode"
fi

cd ../../..
echo "Opening the project workspace in Xcode"
open AlbarakaApp.xcworkspace

````
