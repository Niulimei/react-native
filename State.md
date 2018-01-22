# State(状态)

> 如果需要改变数据就要使用state.     
> 
ES6的写法是在constructor中初始化`state`,然后在需要修改调用`setState`方法。   

例如我们需要制作一段不停闪烁的文字，文字内容本身在组件创建时就已经指定好了，所以文字内容应该是一个`prop`。而文字的显示或隐藏的状态则是随着时间变化的，因此这状态应该写到`state`中。   

```
    import React,{ Component } from 'react';
    import { Text,View } from 'react-native';
    class Blink extends Component{
        constructor(props){
            super(props);
            this.state = { showText:true };
            //每1000毫秒对showText状态做一次取反操作
            setInterval(()=>{
                this.setState(previousState=>{
                    return { showText:!previousState.showText };
                    });
                },1000);
        }
        render(){
            //根据当前showText的值决定是否显示text内容
            let dispaly = this.state.showText?this.props.text:'';
            return (
                <Text>{display}</Text>
                );
        }
    }

    export default class BlinkApp extends Component{
        render(){
            return(
                <View>
                    <Blink text='I love to blink' />
                    <Blink text='Yes blinking is so great' />
                    <Blink text='Why did they ever take this out of HTML' />
                    <Blink text='Look at me look at me' />
                </View>
                )
        }
    }
```

实际开发中，我们一般不会在定时器函数(setInterval、setTimeout等)中来操作state。典型的场景是在接受到服务器返回的新数据，或者在用户输入数据之后。你也可以使用一些"状态容器"比如Redux来统一管理数据流。







