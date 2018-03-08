![Release](https://jitpack.io/v/nirwannursabda/expandable-navigation.svg)
https://jitpack.io/#nirwannursabda/expandable-navigation

# Expandable Navigation
Menu in navigation drawer using expandable list view


Use ExpandableNavigationListView inside layout

```groovy
<com.techatmosphere.expandablenavigation.view.ExpandableNavigationListView
    android:id="@+id/expandable_navigation"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:scrollbars="none"
    android:nestedScrollingEnabled="true"
    android:groupIndicator="@null"
    android:divider="@null"
    />
```

Bind it inside activity
```groovy
navigationExpandableListView
    .init(this)
    .addHeaderModel(new HeaderModel("Beranda", R.drawable.ic_home))
    .addHeaderModel(
        new HeaderModel("Kotak Masuk", R.drawable.ic_mail_outline, true)
            .addChildModel(new ChildModel("Chat"))
            .addChildModel(new ChildModel("Diskusi Produk"))
    )
    .addHeaderModel(new HeaderModel("Keluar", R.drawable.ic_assignment_return))
    .build()
    .addOnGroupClickListener(new ExpandableListView.OnGroupClickListener() {
        @Override
        public boolean onGroupClick(ExpandableListView parent, View v, int groupPosition, long id) {
            navigationExpandableListView.setSelected(groupPosition);

            drawerLayout.closeDrawer(GravityCompat.START);
            return false;
        }
    })
    .addOnChildClickListener(new ExpandableListView.OnChildClickListener() {
        @Override
        public boolean onChildClick(ExpandableListView parent, View v, int groupPosition, int childPosition, long id) {
            navigationExpandableListView.setSelected(groupPosition, childPosition);

            drawerLayout.closeDrawer(GravityCompat.START);
            return false;
        }
    });

navigationExpandableListView.setSelected(0);
```

Download
--------

```groovy
buildscript {
  repositories {
    jcenter()

    maven { url "https://jitpack.io" }
   }
}
```

```groovy
dependencies {
  compile 'com.techatmosphere:expandablenavigation:0.1.0'
}
```

License
-------

    Copyright 2013 Tech Atmosphere

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
