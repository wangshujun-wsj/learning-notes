~~~
let routeData = this.$router.resolve({ path: '/login', query: {  id: id } });
 window.open(routeData.href, '_blank');
~~~