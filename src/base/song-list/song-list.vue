<template>
  <div class="song-list">
    <ul>
      <li  @click="selectItem(song, index)" class="item" v-for="(song, index) in songs" :key="index">
        <div class="content">
          <h2 class="name">{{song.name}}</h2>
          <p class="desc">{{getDesc(song)}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script type="">
export default {
  props: {
    songs: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    getDesc(song) {
      return `${song.singer} . ${song.album}`
    },
    selectItem(item, index) {
      this.$emit('select', item, index)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~common/stylus/variable"
@import "~common/stylus/mixin"
.song-list
  .item
    display flex
    align-content center
    box-sizing border-box
    height 64px
    font-size $font-size-medium
    .content
      flex 1
      line-height 20px
      overflow hidden
      .name
        no-wrap()
        color $color-text
        line-height 1.5
      .desc
        no-wrap()
        margin-top 4px
        color $color-text-d
        line-height 1.5
</style>