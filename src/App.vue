<template>
  <div class="bg-gradient-to-br from-gray-50 to-gray-100 min-h-screen">
    <!-- Header -->
    <header class="fixed top-0 left-0 right-0 bg-white shadow-md z-50">
      <div class="container mx-auto px-4 py-3 flex justify-between items-center">
        <div class="flex items-center gap-3">
          <div class="relative w-10 h-10 overflow-hidden rounded-full border-2 border-teal-500">
            <img src="/src/cv.png" alt="Hawre" class="w-full h-full object-cover" />
          </div>
          <h1 class="text-xl font-bold text-teal-600">Hawre</h1>
        </div>

        <!-- Language Switcher -->
        <div class="flex items-center space-x-2">
          <button
            @click="setLanguage('en')"
            :class="`px-2 py-1 rounded-md text-sm font-medium transition-colors ${
              language === 'en'
                ? 'bg-teal-500 text-white'
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`"
          >
            EN
          </button>
          <button
            @click="setLanguage('de')"
            :class="`px-2 py-1 rounded-md text-sm font-medium transition-colors ${
              language === 'de'
                ? 'bg-teal-500 text-white'
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`"
          >
            DE
          </button>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden md:block">
          <ul class="flex space-x-1">
            <li v-for="item in navItems" :key="item.id">
              <button
                @click="scrollToSection(item.id)"
                :class="`px-3 py-2 rounded-full text-sm font-medium transition-all duration-300 ${
                  activeSection === item.id
                    ? 'bg-teal-500 text-white'
                    : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                }`"
              >
                {{ t(`nav.${item.id}`) }}
              </button>
            </li>
          </ul>
        </nav>

        <!-- Mobile Menu Button -->
        <button @click="isMenuOpen = !isMenuOpen" class="md:hidden text-gray-700">
          <svg
            v-if="isMenuOpen"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="lucide lucide-x"
          >
            <path d="M18 6 6 18" />
            <path d="m6 6 12 12" />
          </svg>
          <svg
            v-else
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="lucide lucide-menu"
          >
            <line x1="4" x2="20" y1="12" y2="12" />
            <line x1="4" x2="20" y1="6" y2="6" />
            <line x1="4" x2="20" y1="18" y2="18" />
          </svg>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isMenuOpen" class="md:hidden bg-white border-t border-gray-200">
        <ul class="py-2 px-4 space-y-2">
          <li v-for="item in navItems" :key="item.id">
            <button
              @click="scrollToSection(item.id)"
              :class="`w-full text-left px-3 py-2 rounded-lg text-sm font-medium ${
                activeSection === item.id
                  ? 'bg-teal-500 text-white'
                  : 'text-gray-700 hover:bg-gray-100'
              }`"
            >
              {{ t(`nav.mobile.${item.id}`) }}
            </button>
          </li>
        </ul>
      </div>
    </header>

    <main class="container mx-auto px-4 pt-24 pb-12">
      <!-- Personal Information Section -->
      <section id="personal" class="mb-12" ref="personalSection">
        <div class="bg-white rounded-3xl shadow-lg overflow-hidden">
          <div class="md:flex">
            <div class="md:w-1/3 bg-teal-500 p-8 flex flex-col items-center justify-center">
              <div
                class="relative w-48 h-48 rounded-full overflow-hidden border-4 border-white shadow-lg mb-4"
              >
                <img src="/src/cv.png" alt="Hawre" class="w-full h-full object-cover" />
              </div>
              <h2 class="text-2xl font-bold text-white text-center">Hawre Kamil</h2>
              <p class="text-teal-100 text-center mt-2">Computer Science Graduate</p>
            </div>

            <div class="md:w-2/3 p-8">
              <h3 class="text-xl font-semibold text-gray-800 mb-6 flex items-center">
                <span class="bg-teal-100 p-2 rounded-full mr-3">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="20"
                    height="20"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    class="text-teal-600"
                  >
                    <path
                      d="M14.5 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7.5L14.5 2z"
                    />
                    <polyline points="14 2 14 8 20 8" />
                    <line x1="16" x2="8" y1="13" y2="13" />
                    <line x1="16" x2="8" y1="17" y2="17" />
                    <line x1="10" x2="8" y1="9" y2="9" />
                  </svg>
                </span>
                {{ t('personal.title') }}
              </h3>

              <div class="grid md:grid-cols-2 gap-4">
                <div class="flex items-start">
                  <span class="bg-gray-100 p-2 rounded-full mr-3 mt-1">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="text-teal-600"
                    >
                      <path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z" />
                      <circle cx="12" cy="10" r="3" />
                    </svg>
                  </span>
                  <div>
                    <p class="text-sm text-gray-500">{{ t('personal.address') }}</p>
                    <p class="text-gray-700">Nordstraße 11, 04575 Neukieritzsch</p>
                  </div>
                </div>

                <div class="flex items-start">
                  <span class="bg-gray-100 p-2 rounded-full mr-3 mt-1">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="text-teal-600"
                    >
                      <path
                        d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"
                      />
                    </svg>
                  </span>
                  <div>
                    <p class="text-sm text-gray-500">{{ t('personal.mobile') }}</p>
                    <a
                      href="tel:+491791170306"
                      class="text-gray-700 hover:text-teal-600 transition-colors"
                      >01791170306</a
                    >
                  </div>
                </div>

                <div class="flex items-start">
                  <span class="bg-gray-100 p-2 rounded-full mr-3 mt-1">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="text-teal-600"
                    >
                      <rect width="20" height="16" x="2" y="4" rx="2" />
                      <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
                    </svg>
                  </span>
                  <div>
                    <p class="text-sm text-gray-500">{{ t('personal.email') }}</p>
                    <a
                      href="mailto:hawre.kamil@zohomail.com"
                      class="text-gray-700 hover:text-teal-600 transition-colors"
                      >hawre.kamil@zohomail.com</a
                    >
                  </div>
                </div>

                <div class="flex items-start">
                  <span class="bg-gray-100 p-2 rounded-full mr-3 mt-1">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="text-teal-600"
                    >
                      <rect width="18" height="18" x="3" y="4" rx="2" ry="2" />
                      <line x1="16" x2="16" y1="2" y2="6" />
                      <line x1="8" x2="8" y1="2" y2="6" />
                      <line x1="3" x2="21" y1="10" y2="10" />
                      <path d="M8 14h.01" />
                      <path d="M12 14h.01" />
                      <path d="M16 14h.01" />
                      <path d="M8 18h.01" />
                      <path d="M12 18h.01" />
                      <path d="M16 18h.01" />
                    </svg>
                  </span>
                  <div>
                    <p class="text-sm text-gray-500">{{ t('personal.dob') }}</p>
                    <p class="text-gray-700">03 December 1991</p>
                  </div>
                </div>

                <div class="flex items-start">
                  <span class="bg-gray-100 p-2 rounded-full mr-3 mt-1">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="text-teal-600"
                    >
                      <path d="M4 15s1-1 4-1 5 2 8 2 4-1 4-1V3s-1 1-4 1-5-2-8-2-4 1-4 1z" />
                      <line x1="4" x2="4" y1="22" y2="15" />
                    </svg>
                  </span>
                  <div>
                    <p class="text-sm text-gray-500">{{ t('personal.nationality') }}</p>
                    <p class="text-gray-700">Kurdish</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Education Section -->
      <section id="education" class="mb-12" ref="educationSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <path d="M22 10v6M2 10l10-5 10 5-10 5z" />
              <path d="M6 12v5c3 3 9 3 12 0v-5" />
            </svg>
          </span>
          {{ t('education.title') }}
        </h2>

        <div class="bg-white rounded-3xl shadow-lg p-8">
          <div class="flex flex-col md:flex-row md:items-center">
            <div class="md:w-1/4 mb-4 md:mb-0">
              <span
                class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
              >
                {{ t('education.graduation') }}
              </span>
            </div>
            <div class="md:w-3/4">
              <h3 class="text-xl font-semibold text-gray-800">{{ t('education.degree') }}</h3>
              <p class="text-gray-600 mt-2">{{ t('education.institution') }}</p>
              <p class="text-gray-500 mt-1">{{ t('education.field') }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Experience Section -->
      <section id="experience" class="mb-12" ref="experienceSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <rect width="20" height="14" x="2" y="7" rx="2" ry="2" />
              <path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16" />
            </svg>
          </span>
          {{ t('experience.title') }}
        </h2>

        <div class="space-y-6">
          <!-- Pharmacy Management System -->
          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  05.2025
                </span>
                <p class="text-gray-500 mt-2">Deutschland – Leipzig</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">Pharmacy Management System</h3>
                <p class="mt-3 text-gray-600">
                  Entwicklung eines Desktop-Pharmacy-Management-Systems zur Verwaltung von
                  Apothekenprozessen, unterstützt durch Künstliche Intelligenz.
                </p>

                <div class="mt-4">
                  <h4 class="font-semibold text-gray-700 mb-2">Verwendete Technologien:</h4>
                  <ul class="text-sm text-gray-600 space-y-1">
                    <li>
                      • Programmiersprache: Java (11+), JavaFX (17+) für die Benutzeroberfläche (mit
                      FXML)
                    </li>
                    <li>• Datenbank: MySQL (8.0+), JDBC mit MySQL Connector/J</li>
                    <li>
                      • Bibliotheken: PasswordUtil (BCrypt/SCrypt), DBUtil (Datenbankverbindungen),
                      Session-Management, ExportUtil (CSV-Export)
                    </li>
                    <li>• Build-Tool: Maven (3.6+) oder Gradle (7.x+)</li>
                    <li>• IDE: Visual Studio mit GPT-4.1</li>
                  </ul>
                </div>

                <div class="mt-4">
                  <h4 class="font-semibold text-gray-700 mb-2">Kernfunktionen:</h4>
                  <ul class="text-sm text-gray-600 space-y-1">
                    <li>
                      • Benutzerverwaltung (Hinzufügen, Bearbeiten, Löschen mit Rollenzuweisung)
                    </li>
                    <li>• Rollenbasierte Zugriffskontrolle (Admin, Apotheker, Inventar)</li>
                    <li>• Medikamenten- und Bestandsverwaltung (Chargen, Ablaufdaten)</li>
                    <li>• Verkaufsabwicklung, Prüfprotokollierung, Berichterstellung</li>
                    <li>• Datenbank-Backup und -Wiederherstellung</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- Previous experiences remain the same -->
          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  03.2020 - 06.2020
                </span>
                <p class="text-gray-500 mt-2">Iraq - Sulaymaneyah</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">
                  {{ t('experience.job1.title') }}
                </h3>
                <ul class="mt-3 space-y-2 text-gray-600">
                  <li>{{ t('experience.job1.description') }}</li>
                  <li class="text-gray-500">{{ t('experience.job1.tech') }}</li>
                </ul>
              </div>
            </div>
          </div>

          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  02.2021 - 03.2021
                </span>
                <p class="text-gray-500 mt-2">Iraq - Sulaymaneyah</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">
                  {{ t('experience.job2.title') }}
                </h3>
                <ul class="mt-3 space-y-2 text-gray-600">
                  <li>{{ t('experience.job2.description') }}</li>
                  <li class="text-gray-500">{{ t('experience.job2.tech') }}</li>
                </ul>
              </div>
            </div>
          </div>

          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  01.2021 - 06.2021
                </span>
                <p class="text-gray-500 mt-2">Iraq - Sulaymaneyah</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">
                  {{ t('experience.job3.title') }}
                </h3>
                <ul class="mt-3 space-y-2 text-gray-600">
                  <li>{{ t('experience.job3.description1') }}</li>
                  <li>{{ t('experience.job3.description2') }}</li>
                  <li>{{ t('experience.job3.description3') }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Social Engagement Section -->
      <section id="social" class="mb-12" ref="socialSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <path
                d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.3 1.5 4.05 3 5.5l7 7Z"
              />
            </svg>
          </span>
          {{ t('social.title') }}
        </h2>

        <div class="space-y-6">
          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  01.2022 - 04.2022
                </span>
                <p class="text-gray-500 mt-2">Belarus - Grodno</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">{{ t('social.job1.title') }}</h3>
                <ul class="mt-3 space-y-2 text-gray-600">
                  <li>{{ t('social.job1.description1') }}</li>
                  <li>{{ t('social.job1.description2') }}</li>
                  <li>{{ t('social.job1.description3') }}</li>
                  <li>{{ t('social.job1.description4') }}</li>
                </ul>
              </div>
            </div>
          </div>

          <div class="bg-white rounded-3xl shadow-lg p-8">
            <div class="flex flex-col md:flex-row">
              <div class="md:w-1/4 mb-4 md:mb-0">
                <span
                  class="inline-block bg-teal-100 text-teal-800 text-sm font-medium px-3 py-1 rounded-full"
                >
                  04.2024 - Present
                </span>
                <p class="text-gray-500 mt-2">Germany - Leipzig</p>
              </div>
              <div class="md:w-3/4">
                <h3 class="text-xl font-semibold text-gray-800">{{ t('social.job2.title') }}</h3>
                <ul class="mt-3 space-y-2 text-gray-600">
                  <li>{{ t('social.job2.description1') }}</li>
                  <li>{{ t('social.job2.description2') }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Skills Section -->
      <section id="skills" class="mb-12" ref="skillsSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <polyline points="16 18 22 12 16 6" />
              <polyline points="8 6 2 12 8 18" />
            </svg>
          </span>
          {{ t('skills.title') }}
        </h2>

        <div class="bg-white rounded-3xl shadow-lg p-8">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <polyline points="16 18 22 12 16 6" />
                  <polyline points="8 6 2 12 8 18" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.programming') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['Java', 'PHP', 'Python', 'JavaScript']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <ellipse cx="12" cy="5" rx="9" ry="3" />
                  <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.databases') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['SQL', 'PL/SQL', 'Oracle', 'MS Access']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <circle cx="12" cy="12" r="10" />
                  <line x1="2" x2="22" y1="12" y2="12" />
                  <path
                    d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"
                  />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.webdesign') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['HTML', 'CSS', 'Bootstrap', 'Vue.js', 'jQuery']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <circle cx="13.5" cy="6.5" r="2.5" />
                  <circle cx="17.5" cy="10.5" r="2.5" />
                  <circle cx="8.5" cy="7.5" r="2.5" />
                  <circle cx="6.5" cy="12.5" r="2.5" />
                  <path d="M12 22v-6" />
                  <path d="M14.5 18h-5" />
                  <path d="M10 14v4" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.graphics') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['Adobe Photoshop', 'Adobe Illustrator', 'Adobe After Effects']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <path d="M14.5 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7.5L14.5 2z" />
                  <polyline points="14 2 14 8 20 8" />
                  <line x1="16" x2="8" y1="13" y2="13" />
                  <line x1="16" x2="8" y1="17" y2="17" />
                  <line x1="10" x2="8" y1="9" y2="9" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.office') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['Microsoft Office', 'Libre Office']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <circle cx="12" cy="12" r="10" />
                  <line x1="2" x2="22" y1="12" y2="12" />
                  <path
                    d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"
                  />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">{{ t('skills.cms') }}</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['WordPress', 'WooCommerce']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <!-- Add this new skill category after the existing ones -->
            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <path d="M12 2a3 3 0 0 0-3 3v7a3 3 0 0 0 6 0V5a3 3 0 0 0-3-3Z" />
                  <path d="M19 10v2a7 7 0 0 1-14 0v-2" />
                  <circle cx="12" cy="19" r="3" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">KI-Tools</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="skill in ['Windsurf', 'Cursor', 'ChatGPT', 'GPT-4.1']"
                  :key="skill"
                  class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <rect x="16" y="16" width="6" height="6" rx="1" />
                  <rect x="2" y="16" width="6" height="6" rx="1" />
                  <rect x="9" y="2" width="6" height="6" rx="1" />
                  <path d="M5 16v-3a1 1 0 0 1 1-1h12a1 1 0 0 1 1 1v3" />
                  <path d="M12 12V8" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">Netzwerk</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm"
                  >Routing & Switching</span
                >
              </div>
            </div>

            <div>
              <div class="flex items-center mb-4">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="text-teal-600 mr-2"
                >
                  <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7.5L14 2z" />
                  <polyline points="14 2 14 8 20 8" />
                  <path d="M16 13H8" />
                  <path d="M16 17H8" />
                  <path d="M10 9H8" />
                </svg>
                <h3 class="text-lg font-semibold text-gray-800">Berichtswerkzeuge</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                <span class="bg-teal-50 text-teal-700 px-3 py-1 rounded-full text-sm">JReport</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Languages Section -->
      <section id="languages" class="mb-12" ref="languagesSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <path d="m5 8 6 6" />
              <path d="m4 14 6-6 2-3" />
              <path d="M2 5h12" />
              <path d="M7 2h1" />
              <path d="m22 22-5-10-5 10" />
              <path d="M14 18h6" />
            </svg>
          </span>
          {{ t('languages.title') }}
        </h2>

        <div class="bg-white rounded-3xl shadow-lg p-8">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="bg-teal-50 rounded-2xl p-6 text-center">
              <h3 class="text-lg font-semibold text-gray-800 mb-2">{{ t('languages.kurdish') }}</h3>
              <p class="text-teal-700">{{ t('languages.kurdish.level') }}</p>
              <div class="mt-4 flex justify-center">
                <div v-for="i in 5" :key="i" class="w-4 h-4 rounded-full bg-teal-500 mx-1"></div>
              </div>
            </div>

            <div class="bg-teal-50 rounded-2xl p-6 text-center">
              <h3 class="text-lg font-semibold text-gray-800 mb-2">{{ t('languages.english') }}</h3>
              <p class="text-teal-700">{{ t('languages.english.level') }}</p>
              <div class="mt-4 flex justify-center">
                <div v-for="i in 4" :key="i" class="w-4 h-4 rounded-full bg-teal-500 mx-1"></div>
                <div class="w-4 h-4 rounded-full bg-gray-300 mx-1"></div>
              </div>
            </div>

            <div class="bg-teal-50 rounded-2xl p-6 text-center">
              <h3 class="text-lg font-semibold text-gray-800 mb-2">{{ t('languages.german') }}</h3>
              <p class="text-teal-700">{{ t('languages.german.level') }}</p>
              <div class="mt-4 flex justify-center">
                <div v-for="i in 4" :key="i" class="w-4 h-4 rounded-full bg-teal-500 mx-1"></div>
                <div class="w-4 h-4 rounded-full bg-gray-300 mx-1"></div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Certificates Section -->
      <section id="certificates" class="mb-12" ref="certificatesSection">
        <h2 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
          <span class="bg-teal-100 p-2 rounded-full mr-3">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="text-teal-600"
            >
              <circle cx="12" cy="8" r="6" />
              <path d="M15.477 12.89 17 22l-5-3-5 3 1.523-9.11" />
            </svg>
          </span>
          {{ t('certificates.title') }}
        </h2>

        <div class="bg-white rounded-3xl shadow-lg p-8">
          <div class="space-y-4">
            <div
              v-for="(cert, index) in certificates"
              :key="index"
              class="flex flex-col md:flex-row md:items-center p-4 border-l-4 border-teal-500 bg-gray-50 rounded-r-lg hover:shadow-md transition-shadow"
            >
              <div class="md:w-1/4 mb-2 md:mb-0">
                <span class="text-teal-600 font-medium">{{ cert.date }}</span>
              </div>
              <div class="md:w-3/4">
                <h3 class="font-semibold text-gray-800">{{ cert.title }}</h3>
                <p class="text-gray-500 text-sm">{{ cert.location }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4 text-center">
        <p>© {{ new Date().getFullYear() }} Hawre Kamil. {{ t('footer.rights') }}</p>
        <p class="mt-2 text-gray-400 text-sm">{{ t('footer.profession') }}</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// State
const language = ref('en')
const activeSection = ref('personal')
const isMenuOpen = ref(false)

// Refs for sections
const personalSection = ref(null)
const educationSection = ref(null)
const experienceSection = ref(null)
const socialSection = ref(null)
const skillsSection = ref(null)
const languagesSection = ref(null)
const certificatesSection = ref(null)

// Navigation items
const navItems = [
  { id: 'personal', label: 'Personal' },
  { id: 'education', label: 'Education' },
  { id: 'experience', label: 'Experience' },
  { id: 'social', label: 'Social' },
  { id: 'skills', label: 'Skills' },
  { id: 'languages', label: 'Languages' },
  { id: 'certificates', label: 'Certificates' },
]

// Certificates data
const certificates = [
  { date: 'March 2018', title: 'Certification of Appreciation by Google', location: 'Iraq' },
  { date: 'May 2019', title: 'Motion Graphic Training Course', location: 'Iraq' },
  { date: 'May 2019', title: 'Business Start-Up Training Course', location: 'Iraq' },
  { date: 'August 2019', title: 'English Pre-Intermediate Certificate', location: 'Iraq' },
  {
    date: 'August 2019',
    title: 'Radio Production and Post-Production Certificate',
    location: 'Iraq',
  },
  { date: '2022', title: 'Certificate of Appreciation by UNICEF', location: 'Belarus' },
  { date: 'June 2024', title: 'Deutsch-Test für Zuwanderer, B1 Certificate', location: 'Germany' },
]

// Translations
const translations = {
  en: {
    // Personal Information
    'personal.title': 'Personal Information',
    'personal.address': 'Address',
    'personal.mobile': 'Mobile',
    'personal.email': 'Email',
    'personal.dob': 'Date of Birth',
    'personal.nationality': 'Nationality',

    // Education
    'education.title': 'Education',
    'education.degree': 'Bachelor of Science',
    'education.field': 'Computer Science - Informatik',
    'education.institution': 'University of Human Development, Slemani, Iraq',
    'education.graduation': '2018',

    // Experience
    'experience.title': 'Professional Experience',
    'experience.job1.title': 'Programming and Implementation of Wholesale Management Systems',
    'experience.job1.description':
      'Development of a stock management system with integrated reporting functions for decision-making',
    'experience.job1.tech': 'Technologies Used: Java 1.8, MySQL Workbench, XAMPP Server, JReport',

    'experience.job2.title': 'Implementation of a Travel Company Website',
    'experience.job2.description':
      'Design of a multilingual website (English, Turkish, Kurdish, Arabic)',
    'experience.job2.tech': 'Technology Used: WordPress',

    'experience.job3.title': 'IT Manager at Codeline Office for Technology',
    'experience.job3.description1': 'Customer consulting for IT issues and solutions',
    'experience.job3.description2': 'Development of advertising and branding strategies',
    'experience.job3.description3': 'Public relations for the company',

    // Social Engagement
    'social.title': 'Social Engagement',
    'social.job1.title': 'Volunteer at UNICEF (School in Refugee Camp)',
    'social.job1.description1': 'Translation/Language mediation',
    'social.job1.description2': 'Children and youth programs',
    'social.job1.description3': 'Educational offers (Math, Art, Music, etc.)',
    'social.job1.description4': 'Psychological support and care',

    'social.job2.title': 'Volunteer at Bahnhofsmission',
    'social.job2.description1': 'Food distribution',
    'social.job2.description2': 'Counseling and support for everyday problems',

    // Skills
    'skills.title': 'Skills',
    'skills.os': 'Operating Systems',
    'skills.programming': 'Programming Languages',
    'skills.databases': 'Databases',
    'skills.webdesign': 'Web Design',
    'skills.graphics': 'Graphic Design',
    'skills.office': 'Office Software',
    'skills.cms': 'CMS',

    // Languages
    'languages.title': 'Languages',
    'languages.kurdish': 'Kurdish',
    'languages.kurdish.level': 'Mother tongue',
    'languages.english': 'English',
    'languages.english.level': 'Very good knowledge (B2)',
    'languages.german': 'German',
    'languages.german.level': 'Very good knowledge (B2)',

    // Certificates
    'certificates.title': 'Courses and Certificates',

    // Navigation
    'nav.personal': 'Personal',
    'nav.education': 'Education',
    'nav.experience': 'Experience',
    'nav.social': 'Social',
    'nav.skills': 'Skills',
    'nav.languages': 'Languages',
    'nav.certificates': 'Certificates',

    // Mobile Navigation
    'nav.mobile.personal': 'Personal Information',
    'nav.mobile.education': 'Education',
    'nav.mobile.experience': 'Professional Experience',
    'nav.mobile.social': 'Social Engagement',
    'nav.mobile.skills': 'Skills',
    'nav.mobile.languages': 'Languages',
    'nav.mobile.certificates': 'Courses and Certificates',

    // Footer
    'footer.rights': 'All rights reserved.',
    'footer.profession': 'Computer Science Graduate | Web Developer',
  },
  de: {
    // Personal Information
    'personal.title': 'Persönliche Angaben',
    'personal.address': 'Adresse',
    'personal.mobile': 'Mobil',
    'personal.email': 'E-Mail',
    'personal.dob': 'Geburtsdatum',
    'personal.nationality': 'Nationalität',

    // Education
    'education.title': 'Schulbildung',
    'education.degree': 'Bachelor of Science',
    'education.field': 'Computer Science - Informatik',
    'education.institution': 'University of Human Development (Slemani - Irak)',
    'education.graduation': '2018',

    // Experience
    'experience.title': 'Berufserfahrung',
    'experience.job1.title': 'Programmierung und Implementierung Großhandelsmanagementsysteme',
    'experience.job1.description':
      'Erstellung eines Systems zur Verwaltung von Lagerbeständen mit integrierten Berichtsfunktionen, die zur Entscheidungsfindung beitragen',
    'experience.job1.tech':
      'Verwendete Technologien: Java 1.8, MySQL Workbench, XAMPP Server, JReport',

    'experience.job2.title': 'Implementierung Travel Company Website',
    'experience.job2.description':
      'Konzipierung einer mehrsprachigen Reisewebsite (englisch, türkisch, kurdisch, arabisch)',
    'experience.job2.tech': 'Verwendete Technologien: WordPress',

    'experience.job3.title': 'IT-Manager: Codeline Office for Technology',
    'experience.job3.description1': 'Kundenberatung für IT-Probleme und -lösungen',
    'experience.job3.description2':
      'Entwicklung von Strategien für Werbung und Markenpositionierung',
    'experience.job3.description3': 'Öffentlichkeitsarbeit für die Firma',

    // Social Engagement
    'social.title': 'Soziales Engagement',
    'social.job1.title': 'Ehrenamt bei UNICEF (Schule im Flüchtlingscamp Belarus)',
    'social.job1.description1': 'Übersetzung/Sprachmittlung',
    'social.job1.description2': 'Kinder- und Jugendangebote',
    'social.job1.description3': 'Schulangebote (Mathematik, Kunst, Musik etc.)',
    'social.job1.description4': 'psychologische Unterstützung/Betreuung',

    'social.job2.title': 'Ehrenamt bei der Bahnhofsmission',
    'social.job2.description1': 'Lebensmittelausgabe',
    'social.job2.description2': 'Beratung/Betreuung bei alltäglichen Problemen',

    // Skills
    'skills.title': 'Fähigkeiten',
    'skills.os': 'Betriebssysteme',
    'skills.programming': 'Programmiersprachen',
    'skills.databases': 'Datenbank',
    'skills.webdesign': 'Webdesign',
    'skills.graphics': 'Grafik Design',
    'skills.office': 'Bürosoftware',
    'skills.cms': 'Content Management Systeme',

    // Languages
    'languages.title': 'Sprachen',
    'languages.kurdish': 'Kurdisch',
    'languages.kurdish.level': 'Muttersprache',
    'languages.english': 'Englisch',
    'languages.english.level': 'sehr gute Kenntnisse (B2)',
    'languages.german': 'Deutsch',
    'languages.german.level': 'sehr gute Kenntnisse (B2)',

    // Certificates
    'certificates.title': 'Kurse und Zertifikaten',

    // Navigation
    'nav.personal': 'Persönlich',
    'nav.education': 'Bildung',
    'nav.experience': 'Erfahrung',
    'nav.social': 'Sozial',
    'nav.skills': 'Fähigkeiten',
    'nav.languages': 'Sprachen',
    'nav.certificates': 'Zertifikate',

    // Mobile Navigation
    'nav.mobile.personal': 'Persönliche Angaben',
    'nav.mobile.education': 'Schulbildung',
    'nav.mobile.experience': 'Berufserfahrung',
    'nav.mobile.social': 'Soziales Engagement',
    'nav.mobile.skills': 'Fähigkeiten',
    'nav.mobile.languages': 'Sprachen',
    'nav.mobile.certificates': 'Kurse und Zertifikaten',

    // Footer
    'footer.rights': 'Alle Rechte vorbehalten.',
    'footer.profession': 'Informatik-Absolvent | Webentwickler',
  },
}

// Translation function
const t = (key) => {
  return translations[language.value][key] || key
}

// Set language
const setLanguage = (lang) => {
  language.value = lang
}

// Scroll to section
const scrollToSection = (sectionId) => {
  const sectionRefs = {
    personal: personalSection,
    education: educationSection,
    experience: experienceSection,
    social: socialSection,
    skills: skillsSection,
    languages: languagesSection,
    certificates: certificatesSection,
  }

  const section = sectionRefs[sectionId]?.value
  if (section) {
    window.scrollTo({
      top: section.offsetTop - 80,
      behavior: 'smooth',
    })
    activeSection.value = sectionId
    isMenuOpen.value = false
  }
}

// Handle scroll to update active section
const handleScroll = () => {
  const sectionRefs = {
    personal: personalSection,
    education: educationSection,
    experience: experienceSection,
    social: socialSection,
    skills: skillsSection,
    languages: languagesSection,
    certificates: certificatesSection,
  }

  for (const [id, ref] of Object.entries(sectionRefs)) {
    if (ref.value) {
      const sectionTop = ref.value.offsetTop - 100
      const sectionHeight = ref.value.offsetHeight

      if (window.scrollY >= sectionTop && window.scrollY < sectionTop + sectionHeight) {
        activeSection.value = id
        break
      }
    }
  }
}

// Lifecycle hooks
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style>
html {
  scroll-behavior: smooth;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 0.5s ease-out forwards;
}

@keyframes pulse {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

.hover-pulse:hover {
  animation: pulse 1s infinite;
}
</style>
