# elasticsearch-sim-plugin
elasticsearch评分插件,基于编辑距离(Levenshtein距离),计算字符串的相似度,返回0-1的分数.<br>
This plugin provides a similarity score(double[0,1]) based on edit distance.<br>
<br>
JDK: 1.8<br>
elasticsearch: 7.6.2<br>
<br>
使用说明 Usage:<br>
1.mvn clean package<br>
2.解压${project.build.directory}/releases/elastic-search-sim-1.0.0.20210304.zip到elasticsearch-7.6.2\plugins\sim,重启elasticsearch.<br>
  unzip ${project.build.directory}/releases/elastic-search-sim-1.0.0.20210304.zip to ${elasticsearch.directory}\plugins\sim , restart elasticsearch.<br>
3.GET /_search<br>
{<br>
    "query": {<br>
        "script_score": {<br>
            "query": {<br>
                "match_all": {}<br>
            },<br>
            "script": {<br>
                "source": "string_similarity",<br>
                "lang": "expert_scripts",<br>
                "params": {<br>
                    "field": "your_field",<br>
                    "term": "field_value"<br>
                }<br>
            }<br>
        }<br>
    }<br>
}<br>
