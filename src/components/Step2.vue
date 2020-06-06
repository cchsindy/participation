<template>
  <div>
    <h2>Step 2</h2>
    <h3>IHSAA Forms for 2020-2021</h3>
    <p>
      * If your student was enrolled at Covenant during 2019-2020 and completed
      the 2019-2020 IHSAA Form, you may skip this step.
    </p>
    <p>
      <i>All images must be in JPEG format (.jpg) and less than 4MB each.</i>
    </p>
    <p v-if="!page1">
      Upload IHSAA form page 1
      <br />
      <input ref="page1" type="file" />
      <button @click="upload(1)">Upload Page 1</button>
    </p>
    <p class="uploaded" v-if="page1">Page 1 uploaded.</p>
    <p v-if="!page2">
      Upload IHSAA form page 2
      <br />
      <input ref="page2" type="file" />
      <button @click="upload(2)">Upload Page 2</button>
    </p>
    <p class="uploaded" v-if="page2">Page 2 uploaded.</p>
    <p v-if="!page3">
      Upload IHSAA form page 3
      <br />
      <input ref="page3" type="file" />
      <button @click="upload(3)">Upload Page 3</button>
    </p>
    <p class="uploaded" v-if="page3">Page 3 uploaded.</p>
    <p v-if="!page4">
      Upload IHSAA form page 4
      <br />
      <input ref="page4" type="file" />
      <button @click="upload(4)">Upload Page 4</button>
    </p>
    <p class="uploaded" v-if="page4">Page 4 uploaded.</p>
    <p v-if="!page5">
      Upload IHSAA form page 5
      <br />
      <input ref="page5" type="file" />
      <button @click="upload(5)">Upload Page 5</button>
    </p>
    <p class="uploaded" v-if="page5">Page 5 uploaded.</p>
    <p class="error" v-if="error">{{ error }}</p>
  </div>
</template>

<script>
import AWS from 'aws-sdk'
import AWSconfig from '@/components/AWS-config'

const endpoint = new AWS.Endpoint('nyc3.digitaloceanspaces.com')
const s3 = new AWS.S3({
  endpoint,
  accessKeyId: AWSconfig.key,
  secretAccessKey: AWSconfig.secret,
})

export default {
  data: () => {
    return {
      error: '',
      page1: '',
      page2: '',
      page3: '',
      page4: '',
      page5: '',
    }
  },
  methods: {
    upload(page) {
      this.error = ''
      let file = this.$refs.page1.files[0]
      switch (page) {
        case 2:
          file = this.$refs.page2.files[0]
          break
        case 3:
          file = this.$refs.page3.files[0]
          break
        case 4:
          file = this.$refs.page4.files[0]
          break
        case 5:
          file = this.$refs.page5.files[0]
          break
      }
      if (file.size < 4000000 && file.type === 'image/jpeg') {
        const blob = file.slice(0, file.size - 1)
        const params = {
          Bucket: 'covenant',
          Key: `ihsaa/${this.$parent.docID}_page${page}.jpg`,
          ContentType: file.type,
          Body: blob,
          ACL: 'public-read',
        }
        s3.upload(params, (err, data) => {
          if (!err) {
            switch (page) {
              case 1:
                this.page1 = data.Location
                break
              case 2:
                this.page2 = data.Location
                break
              case 3:
                this.page3 = data.Location
                break
              case 4:
                this.page4 = data.Location
                break
              case 5:
                this.page5 = data.Location
                break
            }
          }
        })
      } else {
        this.error = 'Image file is either too large or not of supported type.'
      }
    },
  },
}
</script>

<style scoped>
.error {
  color: red;
}
.uploaded {
  color: #4a6830;
  font-weight: bold;
}
</style>
