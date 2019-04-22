<template>
  <el-data-table v-bind="tableConfig"></el-data-table>
</template>

<script>
export default {
  data() {
    return {
      tableConfig: {
        url: '/demo/getList',
        columns: [
          {
            type: 'selection'
          },
          {
            prop: 'name',
            label: '组件名称',
            width: '150'
          },
          {
            prop: 'catogory',
            label: '分类',
            width: '150'
          },
          {
            prop: 'version',
            label: '版本',
            width: '150'
          },
          {
            prop: 'language',
            label: '开发语言',
            width: '150'
          },
          {
            prop: 'lasttime',
            label: '最后更新时间',
            width: '150'
          },
          {
            prop: 'state',
            label: '状态',
            width: '100',
            formatter: row =>
              row.state === '上架' ? (
                <span style="color:green">上架</span>
              ) : (
                <span>下架</span>
              )
          }
        ],
        searchForm: [
          {
            $type: 'input',
            $id: 'name',
            label: '组件名称',
            rules: [
              {
                required: true,
                message: '请输入组件名称',
                trigger: 'blur',
                transform: v => v && v.trim()
              }
            ],
            $el: {
              placeholder: '请输入'
            }
          },
          {
            $type: 'select',
            $id: 'catogory',
            label: '分类',
            rules: [{required: true, message: '请选择分类', trigger: 'blur'}],
            $options: [
              '前端组件',
              '测试子组件',
              '分布式工具',
              '应用服务',
              '数据存储'
            ].map(f => ({label: f, value: f})),
            $el: {
              placeholder: '请选择'
            }
          },
          {
            $type: 'select',
            $id: 'state',
            label: '状态',
            rules: [{required: true, message: '请选择状态', trigger: 'blur'}],
            $options: ['上架', '下架'].map(f => ({label: f, value: f})),
            $el: {
              placeholder: '请选择'
            }
          }
        ],
        form: [
          {
            $type: 'input',
            $id: 'name',
            label: '用户名',
            $attrs: {style: 'width:300px'},
            $el: {
              placeholder: '请输入'
            },
            rules: [
              {
                required: true,
                message: '请输入用户名',
                trigger: 'blur'
              }
            ]
          },
          {
            $type: 'select',
            $id: 'catogory',
            label: '分类',
            $el: {
              placeholder: '请选择'
            },
            $options: [
              '前端组件',
              '测试子组件',
              '分布式工具',
              '应用服务',
              '数据存储'
            ].map(f => ({label: f, value: f})),
            rules: [
              {
                required: true,
                message: '请选择分类',
                trigger: 'blur'
              }
            ]
          },
          {
            $type: 'input',
            $id: 'version',
            label: '版本',
            $attrs: {style: 'width:300px'},
            $el: {
              placeholder: '请输入'
            },
            rules: [
              {
                required: true,
                message: '请输入版本号',
                trigger: 'blur'
              }
            ]
          },
          {
            $type: 'select',
            $id: 'language',
            label: '开发语言',
            $el: {
              placeholder: '请选择'
            },
            $options: ['Javascript', 'Java', 'Node.JS'].map(f => ({
              label: f,
              value: f
            })),
            rules: [
              {
                required: true,
                message: '请选择开发语言',
                trigger: 'blur'
              }
            ]
          },
          {
            $type: 'select',
            $id: 'state',
            label: '状态',
            $el: {
              placeholder: '请选择'
            },
            $options: ['上架', '下架'].map(f => ({label: f, value: f})),
            rules: [
              {
                required: true,
                message: '请选择状态',
                trigger: 'blur'
              }
            ]
          }
        ],
        extraButtons: [
          {
            type: 'primary',
            text: '查看',
            atClick: row => {
              alert('查看')
              return Promise.resolve()
            }
          },
          {
            type: 'normal',
            text: '编辑',
            atClick: row => {
              alert('编辑')
              return Promise.resolve()
            }
          },
          {
            type: 'normal',
            text: '下架',
            atClick: row => {
              alert('下架')
              return Promise.resolve()
            }
          }
        ],
        hasEdit: false,
        dataPath: 'payload.content',
        totalPath: 'payload.totalElement'
      }
    }
  },
  methods: {}
}
</script>
