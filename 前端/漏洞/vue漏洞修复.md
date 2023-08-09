### 使用v-html导致的xss攻击

防止v-html导致的xss攻击可以使用以下两种解决方案

- xss插件 npm install xss，会把除了标签和内容之外的所有东西过滤，比如class
- Vue-dompurify-html 既可以保留样式也能防止xss攻击

