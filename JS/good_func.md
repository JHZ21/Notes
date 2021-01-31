## 

```js
  methods: {
  computeVideoDuration(videoFile) {
      return new Promise((resolve, reject) => {
        const fileurl = URL.createObjectURL(videoFile);
        let videoElm = document.createElement('video');
        videoElm.addEventListener('loadedmetadata', function() {
          resolve(videoElm.duration);
          videoElm = null;
        });
        videoElm.src = fileurl;
      });
    },
    async isSatisfiedVideo(video) {
      if (!video) return false;

      if (
        video.size > 50 * 1024 * 1024 ||
        !/(mp4|quicktime)/i.test(video.type)
      ) {
        // 不超过50M, MP4/MOP格式
        return false;
      }
      this.porgressPerSecond = (75 * 1024 * 1024) / video.size; // 假设0.75M/s
      const duration = await this.computeVideoDuration(video);
      return duration >= 8 && duration <= 48; // 时长8-48s
    }
}
```

