# frozen_string_literal: true

source "https://rubygems.org"

# 明确指定 GitHub Pages 官方 gem（会自动管理兼容的 Jekyll 版本）
gem "github-pages", group: :jekyll_plugins

# 仅保留必要的额外依赖（以下是常见安全组合）
gem "kramdown-parser-gfm"  # GitHub Flavored Markdown 支持
gem "webrick"  # 本地运行 Jekyll 时可能需要

# 注意：csv、bigdecimal、base64、logger 都是 Ruby 标准库
# 不需要在 Gemfile 中声明，直接在代码中 require 即可