<template>
  <div class="hd-timeline">
    <header class="hd-timeline-header" v-if="header" :style="headerStyle">{{header}}</header>
    <div class="hd-timeline-body">
      <el-timeline
        style="padding:0;max-width:100%;flex:auto;align-self:flex-start;"
        v-if="timelineArr&&timelineArr.length>0"
        :reverse="reverse"
      >
        <el-timeline-item
          v-for="activity of timelineArr"
          :key="activity.key"
          :timestamp="activity.timestamp"
          :type="activity.type"
          :color="activity.color"
          :size="activity.size"
          placement="top"
        >
          <el-card>
            <div class="card-title" :class="{'card-title-border-bottom':!!activity.content}">
              <span>{{activity.title}}</span>
              <span>{{activity.userName}}</span>
            </div>
            <p v-if="activity.content">
              <strong>{{activity.content}}</strong>
            </p>
          </el-card>
        </el-timeline-item>
      </el-timeline>
      <span class="defaultTip" v-else :style="defaultTipStyle">{{defaultTip}}</span>
    </div>
  </div>
</template>

<script>
import { Timeline, Card } from "element-ui";

export default {
  components: {
    "el-timeline": Timeline,
    "el-card": Card
  },
  name: "hd-timeline",
  props: {
    header: {
      type: String,
      required: true
    },
    defaultTip: {
      type: String,
      required: true
    },
    headerStyle: String,
    defaultTipStyle: String,
    data: {
      type: Array
    },
    dataMap: {
      type: Object,
      default() {
        return {
          key: "key",
          timestamp: "timestamp",
          type: "type",
          color: "color",
          size: "size",
          title: "title",
          userName: "userName",
          content: "content"
        };
      },
      validator(obj) {
        if (!obj.hasOwnProperty("key")) {
          return false;
        }
        return true;
      }
    },
    reverse: {
      type: Boolean,
      default() {
        return false;
      }
    }
  },
  computed: {
    timelineArr() {
      const arr = [];
      if (this.data.length > 0) {
        for (let data of this.data) {
          this.copyTo(arr, data, this.dataMap);
        }
      }
      return arr;
    }
  },
  methods: {
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
.hd-timeline {
  display: flex;
  flex-direction: column;
  height: inherit;
  max-height: 100%;
  margin: 0;
  border: 1px solid #cfdcf5;
  box-sizing: border-box;
}

.hd-timeline-header {
  box-sizing: border-box;
  margin: 0;
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

.hd-timeline-body {
  flex: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-y: scroll;
  padding: 8px 16px 0;
  margin-bottom: 8px;
  font-size: 12px;
}

.defaultTip {
  font-size: 12px;
  font-weight: 600;
  color: #909399;
}

.card-title {
  color: #909399;
  display: flex;
  justify-content: space-between;
  padding-bottom: 5px;
}

.card-title-border-bottom {
  border-bottom: 1px solid rgb(236, 237, 239);
}

p {
  margin: 0;
  padding: 0;
  margin-top: 1em;
}
</style>