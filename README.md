# 大大大大big创
这是一个“求是学术”大创项目的仓库，我们的项目名称是“质量与票房如何两翼齐飞？——基于四方信号博弈视角下电影市场供需协同的机制研究”。

## 1 数据集描述
为考察电影的“真实质量”（Real Quality）和院线的“排片惯性”（Scheduling Inertia），我们构建了一个多源、高频的电影市场数据库。

### 1.1 电影市场动态面板数据
`/maoyan_panel_raw`下

这是本研究的核心数据集，源自“[猫眼专业版](https://piaofang.maoyan.com/dashboard/movie)”，时间跨度为2024-11-06至2025-11-05，数据频率为每日。

- **结构：** 电影-时间面板数据（Movie-Day Panel Data）。
- **关键变量：**
  - `movieName` (影片名称)：电影的唯一标识符。
  - `releaseInfo` (上映信息)：自首映日起的累计上映天数，为关键的时间序列控制变量。
  - `sumBox` (累计票房)：截至当日的累计票房总额（元）。
  - `grossBoxOffice` (当日票房)：该日的票房收入（元）。
  - `boxOfficeShare` (票房占比)：当日票房占样本/全国总票房的百分比。
  - `showCount` (排片场次)：该片当日全国放映场次，衡量院线资源分配的核心指标。
  - `showShare` (排片占比)：该片当日排片场次占总排片场次的百分比。
  - `avgSeatView` (场均人次)：当日平均每场放映的观影人次。
  - `boxRate` (上座率)：当日观影人次与可售座位数之比（比例/百分比）。
  
### 1.2 电影质量代理数据 
`/box_office_top_lifetime.csv`

为客观衡量“真实质量”，我们收集了“[豆瓣Top250](https://movie.douban.com/top250)”电影的数据。豆瓣评分因其庞大的用户基数和相对中立的算法，常被学术界用作衡量电影艺术和观赏质量的代理变量（Proxy Variable）。

- **结构：** 电影横截面数据。
- **关键变量：**
  - `title` (影片标题)
  - `year` (年份)
  - `country` (制片国家/地区)
  - `genres` (类型)
  - `rating` (评分)：衡量质量的核心指标。
  - `votes` (评价人数)：衡量评分的稳健性（Robustness）和市场关注度。

### 1.3 市场预期与IP价值数据
`/box_office_top_lifetime.csv`

为控制院线在排片时可能存在的“先验信念”（Prior Beliefs）或对头部IP的偏好，我们收集了“[全球票房总榜Top 1000](https://www.boxofficemojo.com/chart/top_lifetime_gross/?area=XWW)”的数据。

- **结构：** 电影横截面数据。
- **关键变量：**
  - `rank` (排名)
  - `title` (影片标题)
  - `gross` (全球票房)
  - `year` (年份)
- **用途：** 此数据用于识别具有高市场预期（例如，知名系列电影的续集）的影片，这些影片的初始排片可能更多地基于其IP价值，而非即时口碑。