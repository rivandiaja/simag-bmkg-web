# Coverage SIMAG di SonarQube Cloud

Jalankan `npm ci --ignore-scripts`, lalu `npm run test:unit:coverage` untuk menjalankan unit test dan membuat `coverage/lcov.info`. GitHub Actions menjalankan perintah yang sama dan scanner mengimpor laporan LCOV dari commit yang dianalisis. [Dokumentasi SonarQube Cloud](https://docs.sonarsource.com/sonarqube-cloud/analyzing-source-code/test-coverage/javascript-typescript-test-coverage)

## Aktifkan analisis berbasis CI

1. Buat token SonarQube Cloud dengan izin menjalankan analisis proyek. Simpan nilainya sebagai repository secret `SONAR_TOKEN` pada **Settings → Secrets and variables → Actions → Secrets** di fork GitHub.
2. Di proyek SonarQube Cloud, buka **Administration → Analysis Method** dan matikan **Automatic Analysis**.
3. Pada tab **Variables** di pengaturan GitHub Actions, buat `SONAR_CI_ENABLED` dengan nilai `true`. Workflow memakai project key `rivandiaja_simag-bmkg-web` dan organisasi `rivandiaja` secara default. Keduanya bisa diubah melalui `SONAR_PROJECT_KEY` dan `SONAR_ORGANIZATION` jika proyek dipindahkan.
4. Buka **Actions → SonarQube → Run workflow**, pilih `main`, lalu jalankan. Setelah analisis selesai, cek commit dan metrik **Coverage** pada tab **Overall Code**. [Dashboard SonarQube Cloud](https://sonarcloud.io/summary/overall?id=rivandiaja_simag-bmkg-web&branch=main)

Log **Run unit tests and generate LCOV** menampilkan coverage di runner GitHub Actions. SonarQube menghitung metrik **Coverage** dari laporan itu dan cakupan kode yang dianalisis.
