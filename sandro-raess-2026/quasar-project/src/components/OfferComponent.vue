<template>
  <div class="q-pa-md">
    <div class="text-h4 text-center q-mb-lg">{{ $t("myServices") }}</div>
    <div class="text-subtitle1 text-center text-grey-7 q-mb-xl">
      {{ $t("myServicesDescription") }}
    </div>

    <div class="row q-col-gutter-lg justify-center q-mb-xl">
      <!-- Visualization Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="palette" size="80px" color="orange" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">Visualization & Design</div>
            <div class="text-body2 text-grey-7">
              Transform your ideas into visual concepts. From wireframes and mockups to
              interactive prototypes, I help bring your vision to life with clear,
              engaging designs.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in visualizationSkills"
              :key="skill"
              color="orange"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>

      <!-- Digitalization Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="cloud_upload" size="80px" color="teal" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">Digitalization</div>
            <div class="text-body2 text-grey-7">
              Convert your analog processes and workflows into efficient digital
              solutions. Streamline operations, reduce paperwork, and modernize your
              business infrastructure.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in digitalizationSkills"
              :key="skill"
              color="teal"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>

      <!-- Consulting Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="lightbulb" size="80px" color="amber" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">Consulting & Strategy</div>
            <div class="text-body2 text-grey-7">
              Get expert advice on your digital transformation journey. Strategic
              planning, technology selection, and implementation roadmaps tailored to your
              business needs.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in consultingSkills"
              :key="skill"
              color="amber"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>
    </div>

    <div class="text-h5 text-center q-mb-lg q-mt-xl">Technologies I Use</div>

    <div class="row q-col-gutter-lg justify-center">
      <!-- Vue.js Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="img:https://vuejs.org/logo.svg" size="80px" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">Vue.js Development</div>
            <div class="text-body2 text-grey-7">
              Building modern, reactive web applications with Vue.js and Quasar. Expertise
              in component-based architectures, state management, and responsive design.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in vueSkills"
              :key="skill"
              color="green"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>

      <!-- .NET Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="code" size="80px" color="purple" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">.NET Development</div>
            <div class="text-body2 text-grey-7">
              Creating robust backend solutions and APIs with .NET. Experience in ASP.NET
              Core, Web APIs, and building scalable enterprise applications.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in dotnetSkills"
              :key="skill"
              color="purple"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>

      <!-- Godot Card -->
      <div class="col-12 col-md-4 col-sm-6" @click="clickOnCard">
        <q-card class="service-card" flat bordered>
          <q-card-section class="text-center q-pt-lg">
            <q-icon name="sports_esports" size="80px" color="blue" />
          </q-card-section>
          <q-card-section>
            <div class="text-h5 text-center q-mb-sm">Godot Game</div>
            <div class="text-body2 text-grey-7">
              Developing engaging games and interactive experiences with Godot Engine.
              Proficient in GDScript, 2D/3D game design, and game mechanics
              implementation.
            </div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-chip
              v-for="skill in godotSkills"
              :key="skill"
              color="blue"
              text-color="white"
              size="sm"
              class="q-ma-xs"
            >
              {{ skill }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>

  <DialogForContactComponent v-model="contactDialogOpen" />
</template>

<script setup lang="ts">
import { ref } from "vue";
import DialogForContactComponent from "./DialogForContactComponent.vue";

const contactDialogOpen = ref(false);

const visualizationSkills = ref(["UI/UX Design", "Wireframing", "Prototyping", "Figma"]);
const digitalizationSkills = ref([
  "Process Automation",
  "Digital Workflows",
  "Cloud Migration",
  "Legacy Modernization",
]);
const consultingSkills = ref([
  "Tech Strategy",
  "Digital Roadmaps",
  "Solution Architecture",
  "Best Practices",
]);

const vueSkills = ref(["Vue 3", "Quasar", "Vuetify", "TypeScript", "Composition API"]);
const dotnetSkills = ref(["ASP.NET Core", "Web API", "C#", "Entity Framework"]);
const godotSkills = ref(["GDScript", "2D", "Game Design", "Godot 4"]);

const clickOnCard = () => {
  contactDialogOpen.value = true;
};
</script>

<style scoped lang="scss">
.service-card {
  height: 100%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;

  &:hover {
    transform: translateY(-8px);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
  }
}
</style>
