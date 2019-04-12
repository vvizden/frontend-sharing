<template>
  <section class="hd-carousel">
    <header v-if="header && header.length>0" class="hd-carousel-header">
      <ul v-if="header.length>1">
        <li
          v-for="(header, index) of header"
          :key="index"
          @click.stop="changeTab(index)"
          :class="{stretch,liHover,active:index===currentTab}"
        >{{header}}</li>
      </ul>
      <ul v-else>
        <li :class="{stretch}">{{header.shift()}}</li>
      </ul>
    </header>
    <main class="hd-carousel-main">
      <el-carousel
        v-if="photos.length>0"
        :interval="4000"
        type="card"
        class="carousel-body"
        height="100%"
      >
        <el-carousel-item v-for="(photo, index) of photos" :key="photo.id" class="box-flex-center">
          <img
            v-if="enablePreview"
            :src="photo.url"
            alt
            style="max-width: 100%;max-height: 100%;"
            @click.stop="previewPhotos(index)"
          >
          <img v-else :src="photo.url" alt style="max-width: 100%;max-height: 100%;">
        </el-carousel-item>
      </el-carousel>
      <span v-else class="default-tip" :style="defaultTipStyle">{{defaultTip}}</span>
    </main>
    <el-dialog title="预览" :visible.sync="imgPreviewDialogVisible" append-to-body top="12vh" width="60%">
      <el-carousel
        :autoplay="false"
        arrow="always"
        :initial-index="initialIndex"
        height="550px"
        indicator-position="outside"
      >
        <el-carousel-item v-for="photo of photos" :key="photo.key" class="box-flex-center">
          <img :src="photo.url" alt style="max-width: 100%;max-height: 100%;">
        </el-carousel-item>
      </el-carousel>
    </el-dialog>
  </section>
</template>

<script>
import { Carousel, CarouselItem, Dialog } from "element-ui";

export default {
  inheritAttrs: false,
  components: {
    "el-carousel": Carousel,
    "el-carousel-item": CarouselItem,
    "el-dialog": Dialog
  },
  name: "hd-carousel",
  props: {
    header: {
      type: Array
    },
    defaultTip: {
      type: String,
      default() {
        return "暂无数据";
      }
    },
    defaultTipStyle: String,
    data: {
      type: Array,
      default() {
        return [];
      }
    },
    dataMap: {
      type: Object,
      default() {
        return {
          key: "key",
          url: "url"
        };
      },
      validator(obj) {
        if (!obj.hasOwnProperty("key")) {
          return false;
        }
        return true;
      }
    },
    enablePreview: {
      type: Boolean,
      default() {
        return false;
      }
    },
    stretch: {
      type: Boolean,
      default() {
        return false;
      }
    }
  },
  data() {
    return {
      currentTab: 0, // 当前tab索引
      initialIndex: 0, // 当前图片索引
      imgPreviewDialogVisible: false // 图片预览对话框
    };
  },
  computed: {
    photos() {
      const arr = [];
      if (this.data.length > 0) {
        const currentPhotoArr = this.data[this.currentTab];
        for(let currentPhoto of currentPhotoArr){
          this.copyTo(arr,currentPhoto,this.dataMap);
        }
      }
      return arr;
    },
    liHover() {
      return this.header.length > 1;
    }
  },
  methods: {
    // 预览图片集
    previewPhotos(index) {
      if (!this.enablePreview) {
        return false;
      }
      this.initialIndex = index;
      this.imgPreviewDialogVisible = true;
    },
    // 改变tab时执行
    changeTab(index) {
      this.currentTab = index;
      this.initialIndex = 0;
    },
    copyTo(arr, srcObj, keyMap) {
      const newObj = {};
      for (let prop in keyMap) {
        if (!srcObj.hasOwnProperty(keyMap[prop])) {
          continue;
        }
        newObj[prop] = srcObj[keyMap[prop]];
      }
      if (Object.keys(newObj).length !== 0) {
        if (newObj.hasOwnProperty("key")) {
          arr.push(newObj);
        }
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.hd-carousel {
  display: flex;
  flex-direction: column;
  height: inherit;
  max-height: 100%;
  overflow: hidden;
  border: 1px solid #cfdcf5;
  box-sizing: border-box;
}

.hd-carousel-header {
  box-sizing: border-box;
  padding: 0 16px;
  height: 30px;
  line-height: 30px;
  font-weight: normal;
  font-size: 13px;
  color: #202325;
  border-bottom: 1px solid #cfdcf5;
  background: #ebf1fd;
  flex: none;
}

.hd-carousel-main {
  flex: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 8px 16px 0;
  margin-bottom: 8px;
  font-size: 12px;
}

.box-flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel-body {
  flex: auto;
  align-self: stretch;
  display: flex;
  flex-direction: column;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  display: flex;
  height: inherit;
  margin-left: -1em;
  margin-right: -1em;
}

li {
  text-align: center;
  padding: 0 1em;
}

li.liHover:hover {
  cursor: pointer;
  color: #409eff;
}

li.active {
  color: #409eff;
}

li.stretch {
  flex: auto;
}

span.default-tip {
  font-size: 12px;
  font-weight: 600;
  color: #909399;
}
</style>