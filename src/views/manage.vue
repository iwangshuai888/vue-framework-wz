<template>
    <div class="animated fadeIn">
        <Row>
            <Col :sm="24" :md="24" :lg="12">
                <h3>景安最牛的后台管理</h3>
                <p>全新VUE打造最新项目</p>
            </Col>
        </Row>

        <Table :columns="columns1" :data="data1"></Table>
    </div>
</template>

<script>

    export default {
        data() {
            return {
                columns1: [
                    {
                        title: '姓名',
                        key: 'name'
                    },
                    {
                        title: '年龄',
                        key: 'age'
                    },
                    {
                        title: '地址',
                        key: 'address'
                    },
                    {
                        title: '操作',
                        key: 'action',
                        width: 150,
                        align: 'center',
                        render: (h, params) => {
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small'
                                    },
                                    style: {
                                        marginRight: '5px'
                                    },
                                    on: {
                                        click: () => {
                                            this.show(params.index)
                                        }
                                    }
                                }, '查看'),
                                h('Button', {
                                    props: {
                                        type: 'error',
                                        size: 'small'
                                    },
                                    on: {
                                        click: () => {
                                            this.remove(params.index)
                                        }
                                    }
                                }, '删除')
                            ]);
                        }
                    }

                ],
                data1: [
                    {
                        name: '李珊',
                        age: 18,
                        address: '脑残'
                    },
                    {
                        name: '梁璐',
                        age: 25,
                        address: '脑残'
                    },
                    {
                        name: '李博文',
                        age: 30,
                        address: '脑残'
                    },
                    {
                        name: '牛纪斌',
                        age: 26,
                        address: '脑残'
                    }
                ]
            }
        },

        methods: {
            show (index) {
                this.$Modal.info({
                    title: '用户信息',
                    content: `姓名：${this.data1[index].name}<br>年龄：${this.data1[index].age}<br>地址：${this.data1[index].address}`
                })
            },
            remove (index) {
                this.data1.splice(index, 1);
            }
        }

    }
</script>