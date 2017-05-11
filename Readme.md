
## js-ps

getInfo可以获取某一个进程的使用信息，返回一个ps的对象。该方法是通过封装ps命令。
故在windows的CMD上不能正常使用。
ps{'user','pid','cpu','mem','vsz','rss','tt','stat','started', 'time'}

## Installation

```
npm install js-ps
```

```js
const ps = require('js-ps');
const info = ps.get(process.pid);//获取该进程的信息

console.log(info.cpu);//进程cpu的使用率
console.log(info.time);//使用时间
/*or(也可以这样使用)*/
ps.get(process.pid,(err,data)=>{
    if(err) throw new Error(e);
    console.log(data.cpu);
    console.log(data.time);
});
//可以查询多个
const pid = [11234,55674];
const info_arr = ps.get((pid);
info_arr[pid[0]].cpu;
info_arr[pid[0]].rss;
/*or(也可以这样使用)*/
ps.get(pid, (err, data)=>{
    pid.forEach((val)=>{
        console.log(data[val].cpu);
    });
})

```

## API

### ps.get(pid[, callback]) pid 可以是number，也可以是array
@return ps{'user','pid','cpu','mem','vsz','rss','tt','stat','started', 'time'}; or @return {'pid':ps,...};

### ps.getOne(pid[, callback]) pid 为number；
@return ps{'user','pid','cpu','mem','vsz','rss','tt','stat','started', 'time'};

### ps.getMany(pid[, callback]) pid 为array；
@return ps{'pid':{'user','pid','cpu','mem','vsz','rss','tt','stat','started', 'time'},...};
