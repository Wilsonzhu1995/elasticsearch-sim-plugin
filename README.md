# elasticsearch-sim-plugin
elasticsearch评分插件,基于编辑距离(Levenshtein距离),计算字符串的相似度,返回0-1的分数.
This plugin provides a similarity score(double[0,1]) based on edit distance.

JDK: 1.8
elasticsearch: 7.6.2

使用说明 Usage:
1.mvn clean package
2.解压${project.build.directory}/releases/elastic-search-sim-1.0.0.20210304.zip到elasticsearch-7.6.2\plugins\sim,重启elasticsearch.
  unzip ${project.build.directory}/releases/elastic-search-sim-1.0.0.20210304.zip to ${elasticsearch.directory}\plugins\sim , restart elasticsearch.
3.GET /_search
{
    "query": {
        "script_score": {
            "query": {
                "match_all": {}
            },
            "script": {
                "source": "string_similarity",
                "lang": "expert_scripts",
                "params": {
                    "field": "your_field",
                    "term": "field_value"
                }
            }
        }
    }
}
