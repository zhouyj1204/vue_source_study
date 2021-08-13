1. 初始化实例， _init

   vm_.isVue  

   如果初始化的参数options._isComponent, 则初始化内部component，initInternalComponent 

   否则将初始化和vm的constructor参数合并为vm.$options

   vm._self = vm

   初始化生命周期所需的attributes

   初始化事件，更新组件的监听事件

   初始化render

   调用beforeCreated函数

   初始化injection

   初始化state

   初始化provide

   调用created函数

   如果vm.$options.el为真，则调用vm.$mount



2. 初始化生命周期的attributes

   ```javascript
   vm.$parent = parent;
   vm.$root = parent ? parent.$root : vm;
   
   vm.$children = [];
   vm.$refs = {};
   
   vm._watcher = null;
   vm._inactive = null;
   vm._directInactive = false;
   vm._isMounted = false;
   vm._isDestroyed = false;
   vm._isBeingDestroyed = false;
   ```



3. init state 根据vm.$options参数初始化

   initProps，对遍历props   key, 定义get set

   initMethods,   options.methods ->   vm[key] = method

   initData  , 对options.data 的数据做proxy处理，get set, 并且生成observer对象， data.__ob__

   initComputed,  生成vm._computedWatchers，并且为每个computedKey 生成一个watcher对象，vm[computedKey]  = func,  为watcher添加dependency 

   initWatch, options.watch生成watcher对象，添加到vm._watchers里
   
   
4. mixin
initMixin(Vue);
stateMixin(Vue);
eventsMixin(Vue);
lifecycleMixin(Vue);
renderMixin(Vue);  

