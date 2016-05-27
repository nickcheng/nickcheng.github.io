---
date: 2004-11-06 04:55:00
type: post
title_en: 2004-11-06-solve-the-bad-cr-in-datagrid
title: DataGrid控件中内容不换行的处理
wordpress_id: 90
tags:
- tech
---

	// ...  
	// 定义DataGrid  
	protected DataGrid myDataGrid;  
	// ...  
	
	// ...  
	// 响应DataGrid的ItemCreated事件  
	myDataGrid.ItemCreated += new System.Web.UI.WebControls.DataGridItemEventHandler(this.DataGrid_ItemCreated);  
	// ...  
	
	// ...  
	// 响应ItemCreated的具体方法  
	// 本方法在每一行被创建的时候响应  
	private void DataGrid_ItemCreated(object sender, System.Web.UI.WebControls.DataGridItemEventArgs e)  
	{ // 在这里, e.Item返回的是当前创建行的对象  
	for(int i = 0; i < e.Item.Cells.Count; i++)  
	{ // e.Item.Cells[x]是当前行中的单元格  
	e.Item.Cells[i].Wrap = false;  
	}  
	}
