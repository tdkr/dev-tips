````java
package com.example.hello.adapter;

import com.example.hello.R;
import com.example.hello.tool.Common;

import android.content.Context;
import android.graphics.Color;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.View.OnClickListener;
import android.view.ViewGroup;
import android.view.ViewGroup.LayoutParams;
import android.widget.AbsListView;
import android.widget.AbsListView.OnScrollListener;
import android.widget.BaseAdapter;
import android.widget.ImageView;
import android.widget.LinearLayout;
import android.widget.ListView;
import android.widget.TextView;
import android.widget.Toast;

public class MyListAdapter extends BaseAdapter implements OnScrollListener {

	class ViewHolder {
		public ImageView animal;
		public TextView cn_word;
		public TextView en_word;
		public ImageView speaker;
	}

	private LayoutInflater mInflater = null;
	private Context context = null;
	private String test = "test";
	private int count = 50;

	public MyListAdapter(Context context) {
		mInflater = (LayoutInflater) context
				.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
		this.context = context;
		
	}
	 
	  

	@Override
	public int getCount() {
		// TODO Auto-generated method stub
		return count;
	}

	@Override
	public Object getItem(int position) {
		// TODO Auto-generated method stub
		return null;
	}

	@Override
	public long getItemId(int position) {
		// TODO Auto-generated method stub
		return position;
	}

	@Override
	public View getView(final int position, View convertView, ViewGroup parent) {

		TextView text = new TextView(context);
		text.setText("this is " + position + "th");
		text.setTextColor(Color.RED);
		text.setTextSize(20);
		text.setOnClickListener(new OnClickListener() {
			@Override
			public void onClick(View v) {
				if (position + 1 == count) {
					count += 50;
					notifyDataSetChanged();
				}
				Common.showMessageWithToast(context, "this item position："
						+ position);
			}

		});
		return text;
		// ViewHolder holder = null;
		// if (convertView == null) {
		// holder = new ViewHolder();
		// convertView = mInflater.inflate(R.layout.fragment_list_item, null);
		// holder.animal = (ImageView) convertView.findViewById(R.id.animal);
		// holder.cn_word = (TextView) convertView.findViewById(R.id.cn_word);
		// holder.en_word = (TextView) convertView.findViewById(R.id.en_word);
		// holder.speaker = (ImageView) convertView.findViewById(R.id.speaker);
		//
		// convertView.setTag(holder);
		// } else {
		// holder = (ViewHolder) convertView.getTag();
		// }
		//
		// holder.animal.setImageResource(R.drawable.ic_launcher);
		// holder.cn_word.setText("xxxxx");
		// holder.en_word.setText("ssssss");
		// holder.speaker.setImageResource(R.drawable.ic_launcher);
		//
		// holder.speaker.setOnClickListener(new OnClickListener(){
		//
		// @Override
		// public void onClick(View v) {
		// System.out.println("Click on the speaker image on ListItem ");
		// }
		// });
		//
		// return convertView;
	}

	@Override
	public void onScroll(AbsListView view, int firstVisibleItem,
			int visibleItemCount, int totalItemCount) {

	}

	@Override
	public void onScrollStateChanged(AbsListView view, int scrollState) {
		switch (scrollState) {
		// 当不滚动时
		case OnScrollListener.SCROLL_STATE_IDLE:
			// 判断滚动到底部
			if (view.getLastVisiblePosition() == (view.getCount() - 1)) {
				Common.showMessageWithToast(context, "滚动到底部");
			}
			// 判断滚动到顶部
			if (view.getFirstVisiblePosition() == 0) {
				Common.showMessageWithToast(context, "滚动到顶部");
			}
			break;
		}
	}

}
````
