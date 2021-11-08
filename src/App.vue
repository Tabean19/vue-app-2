<template>
  <div>
    <TheHeader />
    <button @click="setActiveComp('ActiveGoals')">Active Goals</button>
    <button @click="setActiveComp('ManagedGoals')">Managed Goals</button>
    <keep-alive>
      <component :is="activeComponent"> </component>
    </keep-alive>
    <!-- <BadgeList />
    <UserInfo
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    />
    <CourseGoals #default="slotProperties">
      <h2>{{ slotProperties.item }}</h2>
      <p>{{ slotProperties.otherProps }}</p>
      /* Now we have access to the props defined in the slot */
    </CourseGoals> -->
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
// import BadgeList from './components/BadgeList.vue';
// import UserInfo from './components/UserInfo.vue';
// import CourseGoals from './components/CourseGoals.vue';
import ActiveGoals from './components/ActiveGoals.vue';
import ManagedGoals from './components/ManagedGoals.vue';

export default {
  components: {
    TheHeader,
    ActiveGoals,
    ManagedGoals,
    // BadgeList,
    // UserInfo,
    // CourseGoals,
  },

  data() {
    return {
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
      activeComponent: 'ActiveGoals',
    };
  },
  methods: {
    setActiveComp(component) {
      this.activeComponent = component;
    },
  },
};
</script>

<style scoped>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
