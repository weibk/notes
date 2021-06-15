##  路由懒加载

```javascript
const Home = () => import('../Components/Home');
const About = () => import('../Components/About');
const routers = {
    {
    	path: '/home',
    	component: Home
	},
    {
        path: '/about',
    	component: About
    }
}
```

##  默认路径

```javascript
const routers = [
    {
        path: '',
        redirect: 'home'
    },
    {
    	path: '/Home',
    	component: Home,
    	children: [
            {
                path: '',
                redirect: 'news'
            },
            {
				path: 'news',
                component: HomeNews
            },
            {
                path: 'messages',
                component: HomeMessages
            }
        ]
	},
    {
        path: '/About',
    	component: About
    }
]
```

##  嵌套路由

1. 创建子组件，配置子路由

```javascript
const HomeNews = () => import('../Components/HomeNews');
const HomeMessages = () => import('../Components/HomeMessages');
const routers = [
    {
    	path: '/Home',
    	component: Home,
    	children: [
            {
				path: 'news',
                component: HomeNews
            },
            {
                path: 'messages',
                component: HomeMessages
            }
        ]
	},
    {
        path: '/About',
    	component: About
    }
]
```

2. 在组件中使用`<router-view></router-view>`

##  全局导航守卫

