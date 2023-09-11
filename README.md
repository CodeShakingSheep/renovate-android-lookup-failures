# renovate-android-lookup-failures

This is a minimum reproduction repository to demonstrate dependency lookup failures when creating `renovate.json`. See the corresponding issue [here](https://github.com/renovatebot/renovate/discussions/24314). To reproduce, scan this repository in debug mode for onboarding. 

## Current behavior
Running onboarding PR produces the following warnings:

```
⚠ Dependency Lookup Warnings ⚠
Please correct - or verify that you can safely ignore - these lookup failures before you merge this PR.

Failed to look up maven package com.android.support:appcompat-v7
Failed to look up maven package com.android.support:support-v4
Failed to look up maven package com.android.support:design
Failed to look up maven package com.android.support.constraint:constraint-layout
Failed to look up maven package com.android.support.test:runner
Failed to look up maven package com.android.support.test.espresso:espresso-core
Files affected: build.gradle
```

## Expected bahvior
No warnings should be created but dependencies should be found as they exist in maven repository. E.g., here is the maven artifact for the first dependency [AppCompat-v7](https://mvnrepository.com/artifact/com.android.support/appcompat-v7/28.0.0) including the hint that the artifact is located at Google repository. Here is the [link to the Google repository for the artifact](https://maven.google.com/web/index.html#com.android.support:appcompat-v7:28.0.0). This link also references a [pom.xml](https://dl.google.com/android/maven2/com/android/support/appcompat-v7/28.0.0/appcompat-v7-28.0.0.pom) file which should make a successful lookup possible.

Instead of the warnings, PRs should be created for updating, e.g. from `AppCompat-v7 27.1.1` to `AppCompat-v7 28.0.0`.
