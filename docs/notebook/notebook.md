# Create a new aggregation pipeline notebook example (Work in Progress)

## Install

```
sudo pip install jupyter
sudo pip install numpy scipy pandas scikit-learn tornado pyzmq pygments matplotlib jsonschema
sudo apt-get install pandoc
sudo apt-get install texlive-xetex
```


```
vagrant@devstack:~/juptest$ ls -1 /opt/spark/current/python/lib/py4j* | awk -F "-" '{print $2}'
0.10.4

mkdir -p ~/.local/share/jupyter/kernels/spark2-local
```

```
emacs /home/vagrant/.local/share/jupyter/kernels/spark2-local/kernel.json

{
    "display_name": "spark2-local-compass",
    "language": "python",
    "argv": [
        "/usr/bin/python",
        "-m",
        "IPython.kernel",
        "-f",
        "{connection_file}"
    ],
    "env": {
        "SPARK_HOME": "/opt/spark/current/",
        "PYTHONPATH": "/opt/stack/monasca-transform/:/opt/spark/current/python/:/opt/spark/current/python/lib/py4j-0.10.4-src.zip",
        "PYTHONSTARTUP": "/opt/spark/current/python/pyspark/shell.py",
        "PYSPARK_SUBMIT_ARGS": "--master local[*] --driver-memory 3g --executor-memory 2g pyspark-shell",
        "PYSPARK_PYTHON": "/usr/bin/python"
    }
}
```

## Start

```
mkdir juptest;cd juptest
jupyter notebook --generate-config
jupyter password
jupyter notebook --port 8888 --notebook-dir='/home/vagrant/juptest' --ip='*' --no-browser --log-level=DEBUG  
```

browser:
http://<host>:8888/

e.g.
http://10.0.0.51:8888/

bugs ran into:
http://mail-archives.apache.org/mod_mbox/spark-user/201511.mbox/%3CC2AD9B75-7385-4D4C-A28C-8D29884D46AB@hortonworks.com%3E

## References

[1] https://github.com/ipython/ipython/issues/8612
[2] https://hortonworks.com/hadoop-tutorial/using-ipython-notebook-with-apache-spark/
[3] https://www.youtube.com/watch?v=HW29067qVWk
[4] https://github.com/jupyter/jupyter/wiki/A-gallery-of-interesting-Jupyter-Notebooks
[5] https://krishnan-r.github.io/sparkmonitor/
[6] http://nbviewer.jupyter.org/github/ipython/ipython/blob/1.x/examples/notebooks/Part%203%20-%20Plotting%20with%20Matplotlib.ipynb
[7] https://www.youtube.com/watch?v=Ejh0ftSjk6g




