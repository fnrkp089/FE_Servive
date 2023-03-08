---
description: About Jest
---

# 💚 Testing Library

#### What is Jest ?

💕[JEST](https://jestjs.io/)

Jest 는 코드가 제대로 동작하는 지 확인하는 test case 를 만드는 '테스팅 프레임워크' 이며\
React 뿐만 아니라 `Babel`, `TypeScript`, `Vue`,`Node` 등 다양한 곳에서 사용이  가능하다. \
거의 모든것을 갖춘 테스팅 도구로써 유용하게 사용될것.

Mocking도 다양하게 사용할수 있다.

> 한번도 Jest를 백엔드 했을때도 사용해보지 못햇는데 아쉬웟음...
>
> 또한 아샬님은 모킹을 너무많이 해서 어려울경우에는 설계를 잘못했을 가능성을 내포하고있다고 함.\
> 혹은 현재의 테스트 코드가 핵심 로직이 아니기에 도메인 객체들에게 중요한 분기점을 넘기고있지 않다는 말일수도 있다.

## BDD

```typescript
describe('add', () => {
  it('returns sum of two numbers', () => {
    expect(add(1, 2)).toBe(3);
  });
```



리액트만 테스트하는 코드는 좋지 않다.

테스트 코드를 잘못 작성할시 오히려 테스트코드위주의 코드가 될수 있기 때문에 주의해야한다.\
TDD에서는 상태의 변화, 그로인한 로직, 로직에서 파생되는 변화를 바라봐야지, 모든 UI하나하나 마다 TDD를 적용한다는건, 너무 불필요하다.





