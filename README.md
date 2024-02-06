# big-data-2024-01

https://cwiki.apache.org/confluence/display/HADOOP/Hadoop+Java+Versions
https://www.apache.org/dyn/closer.cgi/hadoop/common/

https://cuddly-blob-cc7.notion.site/Hadoop-Streaming-7a05dbb9afba45c38f12f4e71d09a113

combiner: total = dict()
med=dict()

for line in sys.stdin:
    visit = line.split('\t')
    try:
        total[visit[0]] += int(visit[1])
        med[visit[0]] += 1
    except:
        total[visit[0]] = int(visit[1])
        med[visit[0]] = 1

for item in total:
    print(f'{item} \t{total[item]}\t {med[item]}')

    
reducer: for line in sys.stdin:
    key,value,med=line.strip().split()
    print(f'{key}\t {int(value)/int(med)}')
