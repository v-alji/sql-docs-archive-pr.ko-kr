---
title: 예측 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
ms.openlocfilehash: abca22dbcb9ae6426e839f92e391a658f5029e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647973"
---
# <a name="forecast-table-analysis-tools-for-excel"></a>예측(Excel용 테이블 분석 도구)
  ![테이블 분석 도구 리본의 예측 단추](media/tat-forecast.gif "테이블 분석 도구 리본의 예측 단추")  
  
 **예측** 도구를 사용 하면 Excel 데이터 테이블 또는 다른 데이터 원본의 데이터를 기반으로 예측을 만들고 필요에 따라 각 예측 값과 관련 된 확률을 볼 수 있습니다. 예를 들어 데이터에 날짜 열 및 월의 각 날짜에 해당하는 총 판매를 표시하는 열이 포함된 경우에는 이후 날짜의 판매를 예측할 수 있습니다. 수행할 예측 수를 지정할 수도 있습니다. 예를 들어 5일 또는 30일간 예측할 수 있습니다.  
  
 도구를 완료하면 원본 데이터 테이블 끝에 새 예측이 추가되며 새 값이 강조 표시됩니다. 새 시계열 값은 추가되지 않으므로 예측을 먼저 검토할 수 있습니다.  
  
 또한이 도구는 **예측 보고서**라는 새 워크시트를 만듭니다. 이 워크시트는 마법사가 예측을 성공적으로 수행했는지 여부를 보고합니다. 새 워크시트에는 또한 기록 추세를 보여 주는 꺾은선형 그래프가 포함됩니다.  
  
 시계열을 확장하여 새 예측을 포함시키면 예측 값이 꺾은선형 그래프에 추가됩니다. 기록 값은 실선으로, 예측은 점선으로 표시됩니다.  
  
## <a name="using-the-forecast-tool"></a>예측 도구 사용  
  
1.  예측 가능한 숫자 데이터를 포함하는 Excel 테이블을 엽니다.  
  
2.  **분석** 탭에서 **예측** 을 클릭 합니다.  
  
3.  예측할 열을 지정합니다. 이 도구는 연속 숫자 데이터와 같은 예측 가능한 데이터 형식의 열을 자동으로 선택 합니다. Null 값 또는 0 값이 열에 여러 번 포함되는 경우 누락된 데이터가 결과에 영향을 줄 수 있으므로 이 도구는 연속 숫자 데이터가 있는 일부 열을 선택하지 않을 수 있습니다. 이 문제가 발생 하는 경우 [레이블 재지정 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](relabel-sql-server-data-mining-add-ins.md) 도구를 사용 하 여 데이터를 수정할 수 있습니다.  
  
4.  열에 날짜, 시간 또는 기타 계열 식별자가 포함되도록 지정합니다. 옵션을 선택 하는 경우 **\<no time stamp>** 이 도구는 원본 데이터의 행 순서를 기반으로 계열을 만듭니다.  
  
5.  수행할 예측 수를 지정합니다.  
  
6.  선택적으로 알고리즘에 대한 힌트, 즉 데이터 반복 주기가 매주인지, 매월인지 또는 다른 기간인지를 제공합니다. 데이터가 지정 된 패턴에 맞지 않거나 패턴을 인식 하지 못하는 경우 **\<detect automatically>** 도구가 반복 되는 기간을 찾도록 선택 합니다.  
  
7.  이 마법사는 예측을 원본 테이블에 추가하고 새 워크시트에 예측 보고서를 만듭니다.  
  
8.  예측 그래프에 새 값을 추가하려면 시계열을 확장하여 예측 값을 포함시킵니다.  
  
### <a name="requirements"></a>요구 사항  
 예측하는 열에는 통화 또는 다른 숫자와 같은 연속 숫자 데이터가 있어야 합니다.  
  
 가능한 경우 사용자 데이터에 시간 또는 날짜 계열을 포함하는 열이 있으면 좋습니다. 날짜 및 시간 데이터 대신 숫자 계열 (1, 2, 3 ...)을 사용할 수 있습니다. 그러나 계열 열의 값은 고유해야 합니다. **예측** 도구가 계열 열에서 중복 값을 발견 하면 오류가 발생 합니다.  
  
 **예측** 도구를 사용 하 여 날짜를 예측할 수 없습니다. 오류가 발생하지 않더라도 이 알고리즘은 날짜를 예측 가능한 값으로 사용하도록 설계되지 않았습니다.  
  
### <a name="understanding-time-stamps"></a>타임스탬프 이해  
 *타임 스탬프로*사용할 열을 식별 해야 합니다. 타임스탬프는 두 가지 목적으로 사용됩니다. 첫째, 시계열의 값을 고유하게 식별합니다. 예를 들어 판매량을 매일 추적하는 경우 판매 값이 날짜별로 한 개씩 있어야 합니다. 이 경우 날짜를 타임스탬프로 사용할 수 있습니다. 둘째, 타임스탬프 열은 예측 수행 단위를 나타냅니다. 일일 판매량을 추적하는 경우 예측도 일 단위로 수행됩니다.  
  
 데이터에 날짜나 시간 열이 포함되지 않은 경우 이 도구는 _RowIndex라는 임시 계열 키를 자동으로 만드는데, 이 키는 데이터 집합의 행 순서를 기반으로 합니다.  
  
 예측 수를 지정할 때는 단계 수를 나타내는 정수를 입력합니다. 이러한 단계의 단위는 데이터의 시간 및 날짜 계열에 사용된 단위에 따라 달라집니다. 월별 판매 결과를 나열하는 데이터일 경우 월을 기준으로 예측이 만들어집니다. 시간 단위를 변경하려면 원본 데이터를 변경해야 합니다.  
  
### <a name="understanding-periodicity"></a>주기성 이해  
 예측은 특정 기간 동안 반복되는 패턴을 기반으로 수행됩니다. 따라서 Microsoft Time Series 알고리즘은 가장 강력한 패턴이 있는 기간을 결정하기 위해 계산을 수행합니다. *주기* 는 이러한 기간을 의미 합니다.  
  
 시계열에 잠재적 패턴이 여러 개 포함될 수 있습니다. 데이터에 특정 패턴이 확실히 포함되어 있는 경우 알고리즘에 힌트를 제공하여 예측 품질을 높일 수도 있습니다.  
  
 예를 들어 데이터가 매주 반복될 것으로 예상되는 경우 매주를 선택하여 알고리즘이 주 단위 패턴을 찾도록 지정할 수 있습니다. 그러나 강력한 주 단위 패턴을 찾을 수 없는 경우 알고리즘이 힌트를 무시합니다.  
  
## <a name="understanding-the-forecasting-report"></a>예측 보고서 이해  
 이 그래프에서 사용자 데이터 테이블의 기록 값은 어두운 선으로 표시되며 예측 값은 점선으로 표시됩니다. 선의 한 지점을 클릭하여 예측 값을 볼 수 있습니다.  
  
> [!NOTE]  
>  그래프의 예측 값에 대 한 시간 축에 레이블이 표시 되지 않으면 예측 값이 포함 된 워크시트를 열고 Excel의 **Fill, Series** 함수를 사용 하 여 예측 값을 포함 하도록 타임 스탬프 열을 확장 합니다.  
  
 예측이 요청했던 것보다 적은 수로 분할되는 경우가 있습니다. 일반적으로 이것은 데이터가 부족하여 알고리즘이 더 이상 예측을 진행하지 못했음을 의미합니다. **예측** 도구는 최소 확률 임계값을 충족 하는 예측만 수행 합니다.  
  
## <a name="related-tools"></a>관련 도구  
 Excel용 데이터 마이닝 클라이언트는 고급 데이터 마이닝 기능을 제공하는 별도의 추가 기능이며 예측을 위한 마법사를 포함합니다.  
  
 Excel 용 테이블 분석 도구에 있는 **예측** 도구와 Excel 용 데이터 마이닝 클라이언트의 **예측 마법사는** 시계열 알고리즘을 사용 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .  
  
-   **예측** 도구는 데이터에 가장 적합 한 설정을 사용 하도록 알고리즘을 자동으로 구성 하므로 더 쉽게 사용할 수 있습니다.  
  
-   Excel 용 데이터 마이닝 클라이언트의 **예측** 마법사는 매개 변수를 사용자 지정 하는 기능을 제공 합니다.  
  
 **예측** 마법사에 대 한 자세한 내용은 [예측 마법사 &#40;Excel 용 데이터 마이닝 추가 기능&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)을 참조 하세요. 예측에 사용되는 알고리즘에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 "Microsoft Time Series 알고리즘" 항목을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [Excel용 테이블 분석 도구](table-analysis-tools-for-excel.md)  
  
  