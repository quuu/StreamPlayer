# AgoraStreamPlayer
> A declarative stream player for [agora-rtc-sdk](https://www.agora.io/)

[![Travis][build-badge]][build]
[![npm package][npm-badge]][npm]
[![Coveralls][coveralls-badge]][coveralls]

## Feature
- Declarative stream player controlling stream by props
- Display placeholder for stream without video track
- Label and decorations for stream
- Network Detector to show network status with icon
- Two display mode: cover and contain
- High test coverage

## Quick Start
```bash
npm install agora-stream-player
```

App.js

```
import StreamPlayer from 'agora-stream-player'
import AgoraRTC from 'agora-rtc-sdk'

class Demo extends Component {
  state = {
    stream: null
  }

  componentDidMount() {
    let stream = AgoraRTC.createStream({
      streamID: 1024,
      video: true,
      audio: true
    })
    stream.init(() => {
      this.setState({
        stream
      })
    })
  }

  render() {
    return (
      {/** You'd better use conditional render to make it mount/unmount properly */}
      {this.state.stream && <StreamPlayer
        key={1024} 
        video={true} 
        audio={true} 
        stream={this.state.stream}
        fit="contain"
        label="A stream"  
      />}
    )
  }
}
```

## Props
#### stream: Stream
  Agora stream created by local or subscribed from remote
#### video: boolean
  Enable video or not
#### audio: boolean
  Enable audio or not
#### fit?: "cover" | "contain",
  Use cover or contain display mode
#### networkDetect?: boolean
  Detect network status periodically and show an icon
#### speaking?: boolean
  Mark the speaker with an icon
#### label?: string
  Show some description for the stream
####className?: string,
#### style?: Object

## Develop
## Project setup
```
npm install
```

### Compiles and hot-reloads with a demo
```
npm run start
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Run your tests with coverage
```
npm run test:coverage
```


[build-badge]: https://img.shields.io/travis/menthays/StreamPlayer/master.png?style=flat-square
[build]: https://travis-ci.org/menthays/StreamPlayer

[npm-badge]: https://img.shields.io/npm/v/npm-package.png?style=flat-square
[npm]: https://www.npmjs.org/package/npm-package

[coveralls-badge]: https://img.shields.io/coveralls/menthays/StreamPlayer/master.png?style=flat-square
[coveralls]: https://coveralls.io/github/menthays/StreamPlayer
