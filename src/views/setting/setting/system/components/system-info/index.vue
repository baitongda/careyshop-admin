<template>
  <el-form
    v-if="form"
    :model="form"
    label-width="200px">
    <div v-permission="'/setting/setting/system/info/basis'">
      <el-divider>基础设置</el-divider>

      <el-form-item
        :label="form.name.description"
        prop="name">
        <el-input
          v-model="form.name.value"
          :placeholder="form.name.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.name.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.title.description"
        prop="title">
        <el-input
          v-model="form.title.value"
          :placeholder="form.title.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.title.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.keywords.description"
        prop="keywords">
        <el-input
          v-model="form.keywords.value"
          :placeholder="form.keywords.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.keywords.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.description.description"
        prop="description">
        <el-input
          v-model="form.description.value"
          :placeholder="form.description.description"
          type="textarea"
          :rows="5"/>
        <div class="help-block" v-html="form.description.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.logo.description"
        prop="logo">
        <el-input
          v-model="form.logo.value"
          :placeholder="form.logo.description"
          :clearable="true">
          <template slot="prepend">
            <el-popover
              v-if="form.logo.value"
              width="150"
              placement="top"
              trigger="hover">
              <div class="popover-image">
                <el-image
                  :src="form.logo.value | getPreviewUrl"
                  @click.stop="$preview(form.logo.value)"
                  fit="fill"/>
              </div>
              <i slot="reference" class="el-icon-picture"/>
            </el-popover>
          </template>

          <el-dropdown
            slot="append"
            :show-timeout="50"
            @command="handleCommand">
            <el-button icon="el-icon-upload"/>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item :command="{command: 'storage', source: 'logo'}" icon="el-icon-finished">
                <span>资源选择</span>
              </el-dropdown-item>
              <el-dropdown-item :command="{command: 'upload', source: 'logo'}" icon="el-icon-upload2">
                <span>上传资源</span>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-input>
        <div class="help-block" v-html="form.logo.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.square_logo.description"
        prop="square_logo">
        <el-input
          v-model="form.square_logo.value"
          :placeholder="form.square_logo.description"
          :clearable="true">
          <template slot="prepend">
            <el-popover
              v-if="form.square_logo.value"
              width="150"
              placement="top"
              trigger="hover">
              <div class="popover-image">
                <el-image
                  :src="form.square_logo.value | getPreviewUrl"
                  @click.stop="$preview(form.square_logo.value)"
                  fit="fill"/>
              </div>
              <i slot="reference" class="el-icon-picture"/>
            </el-popover>
          </template>

          <el-dropdown
            slot="append"
            :show-timeout="50"
            @command="handleCommand">
            <el-button icon="el-icon-upload"/>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item :command="{command: 'storage', source: 'square_logo'}" icon="el-icon-finished">
                <span>资源选择</span>
              </el-dropdown-item>
              <el-dropdown-item :command="{command: 'upload', source: 'square_logo'}" icon="el-icon-upload2">
                <span>上传资源</span>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-input>
        <div class="help-block" v-html="form.square_logo.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.information.description"
        prop="information">
        <el-input
          v-model="form.information.value"
          :placeholder="form.information.description"
          type="textarea"
          :rows="5"/>
        <div class="help-block" v-html="form.information.help_text"></div>
      </el-form-item>
    </div>

    <div v-permission="'/setting/setting/system/info/record'">
      <el-divider>备案许可</el-divider>

      <el-form-item
        :label="form.miitbeian.description"
        prop="miitbeian">
        <el-input
          v-model="form.miitbeian.value"
          :placeholder="form.miitbeian.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.miitbeian.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.miitbeian_url.description"
        prop="miitbeian_url">
        <el-input
          v-model="form.miitbeian_url.value"
          :placeholder="form.miitbeian_url.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.miitbeian_url.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.miitbeian_ico.description"
        prop="miitbeian_ico">
        <el-input
          v-model="form.miitbeian_ico.value"
          :placeholder="form.miitbeian_ico.description"
          :clearable="true">
          <template slot="prepend">
            <el-popover
              v-if="form.miitbeian_ico.value"
              width="150"
              placement="top"
              trigger="hover">
              <div class="popover-image">
                <el-image
                  :src="form.miitbeian_ico.value | getPreviewUrl"
                  @click.stop="$preview(form.miitbeian_ico.value)"
                  fit="fill"/>
              </div>
              <i slot="reference" class="el-icon-picture"/>
            </el-popover>
          </template>

          <el-dropdown
            slot="append"
            :show-timeout="50"
            @command="handleCommand">
            <el-button icon="el-icon-upload"/>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item :command="{command: 'storage', source: 'miitbeian_ico'}" icon="el-icon-finished">
                <span>资源选择</span>
              </el-dropdown-item>
              <el-dropdown-item :command="{command: 'upload', source: 'miitbeian_ico'}" icon="el-icon-upload2">
                <span>上传资源</span>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-input>
        <div class="help-block" v-html="form.miitbeian_ico.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.beian.description"
        prop="beian">
        <el-input
          v-model="form.beian.value"
          :placeholder="form.beian.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.beian.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.beian_url.description"
        prop="beian_url">
        <el-input
          v-model="form.beian_url.value"
          :placeholder="form.beian_url.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.beian_url.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.beian_ico.description"
        prop="beian_ico">
        <el-input
          v-model="form.beian_ico.value"
          :placeholder="form.beian_ico.description"
          :clearable="true">
          <template slot="prepend">
            <el-popover
              v-if="form.beian_ico.value"
              width="150"
              placement="top"
              trigger="hover">
              <div class="popover-image">
                <el-image
                  :src="form.beian_ico.value | getPreviewUrl"
                  @click.stop="$preview(form.beian_ico.value)"
                  fit="fill"/>
              </div>
              <i slot="reference" class="el-icon-picture"/>
            </el-popover>
          </template>

          <el-dropdown
            slot="append"
            :show-timeout="50"
            @command="handleCommand">
            <el-button icon="el-icon-upload"/>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item :command="{command: 'storage', source: 'beian_ico'}" icon="el-icon-finished">
                <span>资源选择</span>
              </el-dropdown-item>
              <el-dropdown-item :command="{command: 'upload', source: 'beian_ico'}" icon="el-icon-upload2">
                <span>上传资源</span>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-input>
        <div class="help-block" v-html="form.beian_ico.help_text"></div>
      </el-form-item>
    </div>

    <div v-permission="'/setting/setting/system/info/status'">
      <el-divider>状态设置</el-divider>

      <el-form-item
        :label="form.open_index.description"
        prop="open_index">
        <el-switch
          v-model="form.open_index.value"
          :active-value="1"
          :inactive-value="0">
        </el-switch>
        <div class="help-block" v-html="form.open_index.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.open_mobile.description"
        prop="open_mobile">
        <el-switch
          v-model="form.open_mobile.value"
          :active-value="1"
          :inactive-value="0">
        </el-switch>
        <div class="help-block" v-html="form.open_mobile.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.open_api.description"
        prop="open_api">
        <el-switch
          v-model="form.open_api.value"
          :active-value="1"
          :inactive-value="0">
        </el-switch>
        <div class="help-block" v-html="form.open_api.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.close_reason.description"
        prop="close_reason">
        <el-input
          v-model="form.close_reason.value"
          :placeholder="form.close_reason.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.close_reason.help_text"></div>
      </el-form-item>
    </div>

    <div v-permission="'/setting/setting/system/info/platform'">
      <el-divider>定义平台</el-divider>

      <el-form-item
        v-for="(platform, index) in platforms"
        :label="`${form.platform.description}${index}`"
        :key="`platform_${index}`">

        <el-input
          class="dynamic-platform-key"
          v-model="platform.key"
          placeholder="序列值"
          :clearable="true"/>

        <el-input
          class="dynamic-platform-value"
          v-model="platform.value"
          placeholder="平台名称"
          :clearable="true"/>

        <el-button
          size="small"
          type="text"
          @click.prevent="platforms.splice(index, 1)">删除</el-button>
      </el-form-item>

      <el-form-item size="small">
        <el-button @click="platforms.push({'key': null, 'value': ''})">新增平台</el-button>
        <div class="help-block" v-html="form.platform.help_text"></div>
      </el-form-item>
    </div>

    <div v-permission="'/setting/setting/system/info/cors'">
      <el-divider>跨域访问</el-divider>

      <el-form-item
        v-for="(domain, index) in form.allow_origin.value"
        :label="`${form.allow_origin.description}${index}`"
        :key="`domain_${index}`">
        <el-input
          class="dynamic-domain"
          v-model="form.allow_origin.value[index]"
          placeholder="域名地址"
          :clearable="true"/>

        <el-button
          size="small"
          type="text"
          @click.prevent="form.allow_origin.value.splice(index, 1)">删除</el-button>
      </el-form-item>

      <el-form-item size="small">
        <el-button @click="form.allow_origin.value.push('')">新增域名</el-button>
        <div class="help-block" v-html="form.allow_origin.help_text"></div>
      </el-form-item>
    </div>

    <div v-permission="'/setting/setting/system/info/other'">
      <el-divider>其他设置</el-divider>

      <el-form-item
        :label="form.weixin_url.description"
        prop="weixin_url">
        <el-input
          v-model="form.weixin_url.value"
          :placeholder="form.weixin_url.description"
          :clearable="true"/>
        <div class="help-block" v-html="form.weixin_url.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.qrcode_logo.description"
        prop="qrcode_logo">
        <el-input
          v-model="form.qrcode_logo.value"
          :placeholder="form.qrcode_logo.description"
          :clearable="true">
          <el-dropdown
            slot="append"
            :show-timeout="50"
            @command="handleCommand">
            <el-button icon="el-icon-upload"/>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item :command="{command: 'storage', source: 'qrcode_logo'}" icon="el-icon-finished">
                <span>资源选择</span>
              </el-dropdown-item>
              <el-dropdown-item :command="{command: 'upload', source: 'qrcode_logo'}" icon="el-icon-upload2">
                <span>上传资源</span>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-input>
        <div class="help-block" v-html="form.qrcode_logo.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.third_count.description"
        prop="third_count">
        <el-input
          v-model="form.third_count.value"
          :placeholder="form.third_count.description"
          type="textarea"
          :rows="8"/>
        <div class="help-block" v-html="form.third_count.help_text"></div>
      </el-form-item>

      <el-form-item
        :label="form.card_auth.description"
        prop="card_auth"
        size="small">
        <cs-user-select
          :check-list="form.card_auth.value"
          type-user="admin"
          @confirm="_handleUserConfirm">
          <el-button slot="control">账号选取</el-button>
        </cs-user-select>
        <div class="help-block" v-html="form.card_auth.help_text"></div>
      </el-form-item>
    </div>

    <el-form-item size="small">
      <el-button
        type="primary"
        :loading="loading"
        @click="handleFormSubmit">保存</el-button>
    </el-form-item>

    <cs-storage
      ref="storage"
      style="display: none;"
      :limit="1"
      @confirm="_getStorageFileList">
    </cs-storage>

    <cs-upload
      style="display: none;"
      ref="upload"
      type="slot"
      accept="image/*"
      :limit="1"
      :multiple="false"
      @confirm="_getUploadFileList">
    </cs-upload>
  </el-form>
</template>

<script>
import util from '@/utils/util'
import { setSystemList } from '@/api/config/setting'

export default {
  components: {
    'csUpload': () => import('@/components/cs-upload'),
    'csStorage': () => import('@/components/cs-storage'),
    'csUserSelect': () => import('@/components/cs-user-select')
  },
  data() {
    return {
      loading: false,
      form: null,
      platforms: []
    }
  },
  filters: {
    getPreviewUrl(val) {
      return val ? util.getImageCodeUrl(val) : ''
    }
  },
  methods: {
    // 资源下拉框事件
    handleCommand(command) {
      switch (command.command) {
        case 'storage':
          this.$refs.storage.handleStorageDlg([0, 2], command.source)
          break

        case 'upload':
          this.$refs.upload.handleUploadDlg(command.source)
          break
      }
    },
    // 获取上传资源
    _getUploadFileList(files, source) {
      if (!files.length) {
        return
      }

      const response = files[0].response
      if (!response || response.status !== 200) {
        return
      }

      if (response.data[0].type !== 0) {
        return
      }

      this.form[source].value = source === 'qrcode_logo'
        ? util.checkUrl(response.data[0].url)
        : response.data[0].url
    },
    // 获取选择资源
    _getStorageFileList(files, source) {
      if (!files.length) {
        return
      }

      for (const value of files) {
        if (value.type !== 0) {
          continue
        }

        this.form[source].value = source === 'qrcode_logo'
          ? util.checkUrl(value.url)
          : value.url

        break
      }
    },
    // 选取账号
    _handleUserConfirm(val) {
      this.form.card_auth.value = []
      val.forEach(value => {
        this.form.card_auth.value.push(value.admin_id)
      })
    },
    // 设置配置数据
    setFormData(val) {
      this.form = val
      this.platforms = []

      // eslint-disable-next-line no-unused-vars
      for (const key in this.form.platform.value) {
        if (this.form.platform.value.hasOwnProperty(key)) {
          this.platforms.push({
            'key': key,
            'value': this.form.platform.value[key]
          })
        }
      }
    },
    // 确定修改
    handleFormSubmit() {
      let data = {}
      // eslint-disable-next-line no-unused-vars
      for (const index in this.form) {
        if (this.form.hasOwnProperty(index)) {
          data[index] = this.form[index].value
        }
      }

      let platform = {}
      // eslint-disable-next-line no-unused-vars
      for (const item of this.platforms) {
        platform[item.key] = item.value
      }

      this.loading = true
      data['platform'] = JSON.stringify(platform)

      setSystemList(data)
        .then(() => {
          this.$message.success('操作成功')
        })
        .finally(() => {
          this.loading = false
        })
    }
  }
}
</script>

<style scoped>
  .popover-image {
    text-align: center;
    line-height: 0;
  }

  .popover-image >>> img {
    vertical-align: middle;
    cursor: pointer;
  }

  .el-image >>> .el-image__error {
    line-height: 1.4;
  }

  .dynamic-domain {
    margin-right: 10px;
    width: 320px;
  }

  .dynamic-platform-key {
    margin-right: 10px;
    width: 120px;
  }

  .dynamic-platform-value {
    margin-right: 10px;
    width: 190px;
  }
</style>
