<template>
  <div class="accordion" :class="{ open: isOpen }" v-if="topic">
    <a href="#" class="accordion__header" @click.prevent="isOpen = !isOpen">
        <i :class="topic.fa" aria-hidden="true"></i>
        <span>{{topic.title}}</span>
        <i class="fas fa-chevron-right open-flag" aria-hidden="true"></i>
    </a>
    <ul>
      <li v-for="(link, index) in topic.links" :key="index">
        <a :href="link.url"><i :class="link.fa" aria-hidden="true"></i>{{ link.title }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Accordion',
  props: ['topic'],
  data() {
    return {
      isOpen: false
    };
  }
};
</script>

<style lang="scss" scoped>
.accordion {
  // background-color: white;
  border-bottom: 1px solid rgb(117,190, 233);
  border-radius: 0px;
  font-family: Roboto, sans-serif;
  font-size: 14px;

  &__header {
    display: block;
    padding: 12px 25px;
    color: white;
    text-decoration: none;
    > i:before {
      font-size: 18px;
      margin-right: 15px;
      margin-left: 0;
    }
    > span {
      font-size: 15px;
      color: rgb(158,168,181);
    }
    i.open-flag {
      display:block;
      float: right;
      margin-top: 2px;
      transition: all 0.3s ease-in-out;

      &:before {
        font-size: 13px;
        color: #b0b8c2;
        margin-right: 0;
      }
    }
  }

  &.open {
    > ul {
      max-height: 1000px;
      transition: max-height 650ms ease-in-out;
    }
    > a > span {
     color: white;
    }
    i.open-flag {
      transform: rotate(90deg);
      transition: all 0.3s ease-in-out;
      &:before {
        color: #75bee9;
      }
    }
  }

  > ul {
    display: block;
    background: linear-gradient(to right, #75bee9, #0074c8);
    box-sizing: border-box;
    list-style: none;
    margin: 0;
    padding: 0 20px;
    max-height: 0;
    overflow: hidden;
    transition: max-height 350ms cubic-bezier(0, 1, 0, 1);
    backface-visibility: hidden;
    transform: scale(1);

    > li {
      display: block;
      color: #042158;
      padding: 10px 15px;
      //border-bottom: 1px solid #bfbfbf;

      &:first-child {
        margin-top: 10px;
      }

      &:last-child {
        margin-bottom: 10px;
      }

      a {
        color: rgb(0,116,200);
        font-weight: bold;
        text-decoration: none;
        > i {
          font-size: 14px;
          margin-right: 10px;
          margin-left: 0;
        }
        &:hover {
          color: rgb(0, 100, 184);
          text-decoration: underline;
        }
      }
    }
  }
}
</style>
