---
title: "Main Concept"
---

Bara is designed to establish a standard way we use JavaScript library. Each Bara application is constructed from two main concepts: Stream and Trigger.

# Stream

A Stream is an event factory where will emit a stream of events during runtime. A Stream is a source emitter of an event.

## useStream

Check the example beblow for Stream creation of a simple Timer:

```javascript
import {useStream} from 'bara';

function useTimerStream(delta) {
  const streamName = 'com.example.timer';
  const TIMER_ELAPSED = createEventType('TIMER_ELAPSED');
  return useStream(({setName, addEventType, emit}) => {
    setName(streamName);
    addEventType(TIMER_ELAPSED);
    
    const timer = setInterval(() => {
      emit(TIMER_ELAPSED);
    }, delta)
    
    return () => {
      clearInterval(timer);
    }
  })
}
```

Let's break down what we do above:

1. We defined our Stream factory called `useTimerStream`  as a Stream hook to our Bara application, this function will hold all the event emitter job.


