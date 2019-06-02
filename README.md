pre commit check
下载依赖：
js相关依赖
"babel-eslint": "^10.0.1",
"eslint": "^5.16.0",
"eslint-config-standard": "^12.0.0",
"eslint-friendly-formatter": "^4.0.1",
"eslint-import-resolver-webpack": "^0.11.1",
"eslint-loader": "^2.1.2",
"eslint-plugin-import": "^2.17.3",
"eslint-plugin-node": "^9.1.0",
"eslint-plugin-promise": "^4.1.1",
"eslint-plugin-react": "^7.13.0",
"eslint-plugin-standard": "^4.0.0",
"husky": "^2.3.0",
"lint-staged": "^8.1.7",

css相关依赖
"stylelint": "^10.0.1",
"stylelint-config-standard": "^18.3.0"

创建.stylelintrc配置文件，校验css
{
  "extends": "stylelint-config-standard",
  "rules": {
  }
}

创建.eslintrc配置文件，校验js
{
  "extends": "standard",
  "plugins": ["react"],
  "rules": {
    "no-unused-vars": 0
  }
}

package.json配置
以下都是添加的配置，跟现有的配置不冲突
{
  "scripts": {
    "lint-staged": "lint-staged"
  },
  "husky": {
    "hooks": {
      "pre-commit": "npm run lint-staged"
    }
  },
  // 具体的校验规则
  "lint-staged": {
    "src/*.js": "eslint --ext .js",
    "src/*.css": "stylelint"
  },
}
