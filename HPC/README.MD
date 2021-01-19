
a['a_b'] = a['a'].astype("str") + "_" + a['b'].astype("str")
a['a_b_category'] = a['a_b'].astype("category")
a.groupby(['a_b_category'])['c'].cumsum()
