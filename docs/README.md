# Headline

> An awesome project.



  **{docsify-updated}**  



```java
package com.kingdee.bi.web.actions.operation.monitor;

import com.kingdee.bi.monitor.service.MonitorService;
import com.kingdee.bi.web.actions.BiBaseAction;
import org.springframework.beans.factory.annotation.Autowired;

/**
 * 运营检测
 *
 * @author Sky
 * @date 2019-11-14 15:30.
 */
public class MonitorAction extends BiBaseAction {

    private String menuId;
    private String startDate;
    private String endDate;
    private String tab;
    /** 日期类型；天、周、月 */
    private String dateType;

    @Autowired
    private MonitorService monitorService;

    @Override
    public void prepare() throws Exception {
        setHtmlPageTitle("运营检测");
    }

    /**
     * 关键指标
     * @throws Exception
     */
    public void keyIndicator() throws Exception {
        if (paramIsNull(menuId, startDate, endDate)) {
            return;
        }
        sendCommonData(monitorService.getKeyIndicator(menuId, startDate, endDate));
    }

    /**
     * 指标趋势
     * @throws Exception
     */
    public void indicatorTrend() throws Exception {
        if (paramIsNull(menuId, startDate, endDate, tab)) {
            return;
        }
        sendCommonData(monitorService.getIndicatorTrend(menuId, tab, dateType, startDate, endDate));
    }

    public void setMenuId(String menuId) {
        this.menuId = menuId;
    }

    public void setStartDate(String startDate) {
        this.startDate = startDate;
    }

    public void setEndDate(String endDate) {
        this.endDate = endDate;
    }

    public void setTab(String tab) {
        this.tab = tab;
    }

    public void setDateType(String dateType) {
        this.dateType = dateType;
    }
}

```

