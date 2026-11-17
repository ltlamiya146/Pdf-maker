# GitHub দিয়ে PDF PLUS APK Build করার নিয়ম

## ১) ZIP Extract করুন

`PDF-PLUS-GitHub-Build-Ready.zip` ফোন/কম্পিউটারে Extract করুন। Extract করা ফোল্ডারের ভেতরে `app`, `gradle`, `.github`, `gradlew`, `settings.gradle.kts` এবং `build.gradle.kts` সরাসরি দেখা উচিত।

## ২) GitHub Repository-তে Upload করুন

- GitHub-এ আপনার `Pdf-maker` repository খুলুন।
- Repository root-এ আগের ZIP ফাইলটি রেখে শুধু সেটি Upload করবেন না।
- Extract করা project-এর **ভেতরের সব ফাইল ও ফোল্ডার** repository root-এ Upload করুন।
- GitHub root-এ `app/`, `gradle/`, `.github/`, `gradlew`, `settings.gradle.kts` থাকতে হবে।
- `.github/workflows/main.yml`-এর পুরোনো ফাইল থাকলে সেটি নতুন ZIP-এর ফাইল দিয়ে Replace করুন।

## ৩) APK Build করুন

- GitHub repository-এর **Actions** tab খুলুন।
- **Build PDF Plus APK** workflow নির্বাচন করুন।
- **Run workflow** চাপুন এবং `main` branch নির্বাচন করুন।
- Build শেষ হওয়া পর্যন্ত অপেক্ষা করুন।
- সবুজ টিক এলে workflow run খুলে **Artifacts** থেকে `PDF-PLUS-debug-apk` ডাউনলোড করুন।

## ৪) Build ব্যর্থ হলে

লাল X-সহ run খুলুন। প্রথম যে step লাল হয়েছে সেটি expand করে error-এর শুরু থেকে screenshot দিন। শুধু `BUILD FAILED`-এর শেষ লাইন যথেষ্ট নয়।

## গুরুত্বপূর্ণ

- এই workflow Debug APK তৈরি করে; Play Store-এর জন্য signed Release APK/AAB নয়।
- Release signing key বা password GitHub-এ public করে আপলোড করবেন না।
- এই ZIP-এর workflow Android SDK Platform 36, Build Tools 36.0.0, JDK 17 এবং project-এর Gradle Wrapper ব্যবহার করে।
