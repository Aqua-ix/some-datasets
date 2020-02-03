# 推薦システム用データセット
# セットアップ
[ここ](http://eigen.tuxfamily.org/index.php?title=Main_Page)よりEigenをダウンロード
ダウンロードしたディレクトリで以下を実行

```
$ tar xf eigen-eigen-[任意のバージョン名].tar.bz2
$ cd eigen-eigen-[任意のバージョン名]/
$ sudo cp -r Eigen/ /usr/local/include/
```

# データ整形
各データをダウンロード後、`data`ディレクトリに格納。

各データのディレクトリで端末を開き
```
make.sh
```
を実行。

`[データ名].cxx`の中でデータの整形条件を指定可能。

sparseファイルにするには、

```
g++ -std=c++17 sparse.cxx ; ./a.out [データディレクトリ]/[データファイル(.txt)] [行数] [列数]
```

を実行。

# データセット詳細

## MovieLens100k
943 users 1682 movies 100,000 ratings(1-5)

Available from: 

http://files.grouplens.org/datasets/movielens/ml-100k-README.txt

## MovieLens1M
6,040 users 3,900 movies 1,000,209 ratings

(欠番を詰めると 6,040 users 3706 movies)

Available from: 

http://files.grouplens.org/datasets/movielens/ml-1m-README.txt

## MovieLens10M
71,567 users 10681 movies 10,000,054 ratings

(欠番を詰めると 69,878 users 10,677 movies)

Available from: 

http://files.grouplens.org/datasets/movielens/ml-10m-README.html

## BookCrossing
278,858 users 271,379 books 1,149,780 ratings

Available from: 

http://www2.informatik.uni-freiburg.de/~cziegler/BX/

## Jester
Over 1.7 million continuous ratings (-10.00 to +10.00) of 150 jokes from 59,132 users

(欠番を詰めると 59,132 users 140 jesters)

(マイナスになる評価値を正にするため全体に+11する)

Available from: 

http://www.ieor.berkeley.edu/~goldberg/jester-data/

http://eigentaste.berkeley.edu/dataset/archive/jester_dataset_2.zip

## Libimseti
135,359 users 168,791 profiles 17,359,346 ratings

http://www.occamslab.com/petricek/data/

## Epinions
49,290 users who rated a total of 139,738 different items at least once, 664,824 reviews

(欠番を詰めると 40163 users 139738 reviews)

Available from: 

http://www.trustlet.org/epinions.html

http://www.trustlet.org/datasets/downloaded_epinions/ratings_data.txt.bz2

## Sushi
5,000 users 100 items 

元データでは-1が未評価,0が最低評価の5段階評価となっているので全体に+1をする,一人あたり評価数10で固定

Available from: 

http://www.kamishima.net/sushi/

http://www.kamishima.net/asset/sushi3-2016.zip

## データ整形前

|データ名|ユーザ数|アイテム数|要素数|
|:---|:---|:---|:---|
|**[MovieLens100k](http://files.grouplens.org/datasets/movielens/ml-100k.zip)**|943|1682|100000|
|**[MovieLens1M](http://files.grouplens.org/datasets/movielens/ml-1m.zip)**|6040|3900|1000209|
|**[MovieLens10M](http://files.grouplens.org/datasets/movielens/ml-10m.zip)**|71567|10681|10000054|
|**[Book-Crossing](http://www2.informatik.uni-freiburg.de/~cziegler/BX/BX-CSV-Dump.zip)**|278858|271379|1149780|
|**[Jester](http://eigentaste.berkeley.edu/dataset/archive/jester_dataset_2.zip)**|59132|140|59132|
|**[Libimseti](http://www.occamslab.com/petricek/data/ratings.dat)**|135359|168791|17359346|
|**[Epinions](http://www.trustlet.org/datasets/downloaded_epinions/ratings_data.txt.bz2)**|49290|139738|664824|
|**[Sushi](http://www.kamishima.net/asset/sushi3-2016.zip)**|5000|100|500000|

## データ整形条件

以下の評価数以上の評価があるユーザ・アイテムに絞る

[データ整形参考論文](https://pdfs.semanticscholar.org/422b/b819d88b579ec56b52e385c031ec4893afdb.pdf)

|データ名|ユーザ数|アイテム数|
|:---|:---|:---|
|MovieLens100k|20|50|
|MovieLens1M|200|240|
|MovieLens10M|600|300|
|Book-Crossing|15|8|
|Book-Crossing2|8|4|
|Jester|128|0|
|Jester2|64|0|
|Libimseti|224|224|
|Libimseti2|212|212|
|Epinions|24|24|
|Epinions2|12|12|
|Sushi|0|0|

## データ整形後

|データ名|ユーザ数|アイテム数|要素数|
|:---|:---|:---|:---|
|**[MovieLens100k](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/movie/sparse_movielens874_598.txt)**|874|598|82275|
|**[MovieLens1M](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/movie/sparse_movielens1m905_684.txt)**|905|684|277546|
|**[MovieLens10M](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/movie/sparse_movielens10m1299_1695.txt)**|1299|1695|1022610|
|**[Book-Crossing](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/book/sparse_bookcrossing1091_2248.txt)**|1091|2248|35179|
|**[Book-Crossing2](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/book/sparse_bookcrossing4480_11395.txt)**|4480|11395|112359|
|**[Jester](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/jester/sparse_jester2916_140.txt)**|2916|140|373338|
|**[Jester2](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/jester/sparse_jester7878_140.txt)**|7878|140|811099|
|**[Libimseti](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/libimseti/sparse_libimseti866_1156.txt)**|866|1156|400955|
|**[Libimseti2](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/libimseti/sparse_libimseti1764_2123.txt)**|1764|2123|807105|
|**[Epinions](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/epinions/sparse_epinions1022_835.txt)**|1022|835|42808|
|**[Epinions2](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/epinions/sparse_epinions8282_6606.txt)**|8282|6606|251278|
|**[Sushi](https://github.com/Aqua-ix/some-datasets/blob/master/2019_recom_datasets/sushi/sparse_sushi5000_100.txt)**|5000|100|500000|
