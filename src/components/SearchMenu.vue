<template>
  <div class="search-container">
    <div class="input-container">
      <input @focusin="toggleSearch" @focusout="toggleSearch" type="text" placeholder="ketchupsoppa"/>
        <transition name="slide-fade">
          <div class="search-menu" v-if="searchOpen">
            <ul>
              <li>Ketchupsoppa</li>
              <li>Ketchupsoppa med sting</li>
              <li>Ketchupsoppa med klös</li>
            </ul>
          </div>
        </transition>
    </div>
    <SearchIcon />
  </div>
</template>

<script lang="ts">
import SearchIcon from './SearchIcon.vue';

export default {
  components: {
    SearchIcon,
  },
  name: 'Search-Focus',
  data() {
    return {
      searchOpen: false,
    };
  },
  methods: {
    toggleSearch() {
      this.searchOpen = !this.searchOpen;
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../scss/style.scss';

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from {
  transform: translateY(-40px);
  opacity: 0;
}
.slide-fade-leave-to {
  transform: translateX(50px);
  opacity: 0;
}

.search-container {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-inline-end: 1rem;

  .input-container {
    position: relative;

    input {
      // margin-top: 5px;
      width: 150px;
      height: 31px;
      background-color: #dad0b27c;
      border-radius: 5px;
      border: 1px solid black;
      font-family: $secondaryFont;
      box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
      // margin-bottom: 2px;
      padding-left: 5px;
    }
  }

  .search-menu {
    background-color: #d9d9d9;
    border-radius: 8px;
    border: 1px solid black;
    z-index: 50;
    position: absolute;
    margin-left: -100px;
    height: 185px;
    ul {
      padding: 10px;
      li {
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
        padding-left: 5px;
        color: #530a02;
        display: flex;
        flex-direction: column;
        justify-content: center;
        background-color: #dad0b27c;
        border-radius: 5px;
        border: 1px solid black;
        font-family: $secondaryFont;
        list-style: none;
        width: 230px;
        height: 35px;
        text-decoration: underline;
        margin: auto;
        margin-bottom: 15px;
      }
    }
  }
}

@media screen and (min-width: 740px) {
  input {
    width: 210px;
  }
}

@media screen and (min-width: 1400px) {
  input {
    width: 339px;
  }
}
</style>
