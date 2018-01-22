# Props（属性）

> 大多数组件在创建时就可以使用各种参数来进行定制。用于定制的这些参数就称为`props`（属性）。  
> 

以常见的基础组件Image为例，在创建一个图片时，可以传入一个名为`source`的prop来指定要显示的图片的地址，以及使用名为`style`的prop来控制其尺寸。     


```
    import React,{Component} from 'react';
    import { Image } from 'react-native';

    export default class Bananas extends Component{
        render(){
            let pic = {
                uri:'https://upload.wikinedia.org//wikipedia/commons/d/de/Bananavarieties.jpg'
            };
            return (
                <Image source={pic} style={{with:193,height:110}} />
                );
        }
    }

```

注意`{pic}` 外围有一层括号，我们需要用括号把`pic` 这个变量嵌入到JSX语句中。括号的意思是括号内部为一个js变量或表达式，需要执行后取值。因此我们可以把任意合法的JavaScript表达式通过括号嵌入到JSX语句中。     

自定义的组件也可以使用`props`。通过在不同的属性制定，可以尽量提高自定义组件的复用范畴。只需要
`render`函数中引用`this.props`，然后按需处理即可。例如：  

```
    import React,{Component} from 'react';
    import { Text,View } from 'react-native';

    class Greeting extends Component{
        render(){
            return(
                <Text>Hello {this.props.name}!</Text>
            );
        }
    }

    export default class LotsOfGreetings extends Component{
        render(){
            return(
                <View style={{alignItems:'center'}}>
                    <Greeting name='Rexxar' />
                    <Greeting name='Jaina' />
                    <Greeting name='Valeera' />
                </View>
            )
        }
    }

```

我们在`Greeting`组件中将`name` 作为一个属性来制定，这样可以复用这一组件来制作各种不同的“问候语”。上面的例子把`Greeting` 组件写在JSX语句中，用法和内置组件并无二致--这正是React体系的魅力所在。  

上面的例子出现了一样新的名为`View`的组件。`View`常用作其他组件的容器，来帮助控制布局和样式。








