---
title: 포함된 데이터 세트 및 공유 데이터 세트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: adc95cc0-d15a-413d-bc5a-302eab37a069
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21b6136433d3fca56f3a98825e3d0ab9c0cf42e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742884"
---
# <a name="embedded-and-shared-datasets-report-builder-and-ssrs"></a>포함된 데이터 세트 및 공유 데이터 세트(보고서 작성기 및 SSRS)
  보고서에서 데이터 세트는 외부 데이터 원본에 대해 쿼리를 실행할 때 반환되는 보고서 데이터를 나타냅니다. 데이터 세트는 외부 데이터 원본에 대한 정보를 포함하는 데이터 연결에 따라 달라집니다. 이때 데이터 자체가 보고서 정의에 포함되지는 않습니다. 데이터 세트에는 쿼리 명령, 필드 컬렉션, 매개 변수, 필터 및 대/소문자 구분, 데이터 정렬 등의 데이터 옵션이 포함됩니다. 데이터 세트에는 두 가지 유형이 있습니다.  
  
-   **공유 데이터 세트.** 공유 데이터 세트는 보고서 서버에 게시되며 여러 보고서에서 사용할 수 있습니다. 공유 데이터 세트는 공유 데이터 원본을 기반으로 해야 합니다. 공유 데이터 세트는 캐시 새로 고침 계획을 만들어 캐시하고 예약할 수 있습니다.  
  
-   **포함된 데이터 세트.** 포함된 데이터 세트는 단일 보고서에서 정의되고 사용됩니다.  
  
 두 유형 간의 차이점은 연결 문자열이 작성, 저장 및 관리되는 방법입니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="shared-datasets"></a>공유 데이터 세트  
 공유 데이터 세트를 사용하여 둘 이상의 보고서에서 사용할 수 있는 쿼리를 제공할 수 있습니다. 공유 데이터 세트는 보고서 서버에 저장되며 보고서나 공유 데이터 원본과는 별도로 관리됩니다. 예를 들어 보고서 서버 관리자가 향상된 인덱싱이나 기타 쿼리 성능 최적화를 사용하도록 쿼리를 업데이트할 수 있습니다.  
  
 가능한 한 공유 데이터 세트를 많이 사용하는 것이 좋습니다. 그러면 쿼리를 최적화하거나 쿼리 결과를 캐시하여 보고서 성능을 향상시킬 수 있습니다. 공유 데이터 세트를 사용하면 데이터 액세스 관리가 더 쉬울 뿐만 아니라 보고서 및 보고서에서 액세스하는 데이터 세트를 더욱 안전하고 향상된 성능으로 유지할 수 있습니다.  
  
 보고서 디자이너에서는 보고서 프로젝트의 일부로 공유 데이터 세트를 만들고 이를 보고서 서버에 배포할지 여부를 제어할 수 있습니다. 보고서 서버를 찾을 수 없으며 공유 데이터 세트를 선택하여 보고서에 추가할 수 없습니다.  
  
 보고서 작성기에서 다음을 수행할 수 있습니다.  
  
1.  공유 데이터 세트를 만들려면 공유 데이터 세트 디자인 뷰를 사용합니다. 이 뷰를 보고서 서버나 SharePoint  사이트에 저장하여 다른 보고서와 공유할 수 있습니다. 보고서 서버를 찾아 기존의 공유 데이터 세트를 편집할 수도 있습니다. 이 뷰에서는 쿼리를 작성하고 모든 데이터 세트 옵션을 설정할 수 있습니다. 자세한 내용은 [공유 데이터 세트 디자인 뷰&#40;보고서 작성기&#41;](../report-builder/shared-dataset-design-view-report-builder.md)를 참조하세요.  
  
2.  보고서에 공유 데이터 세트를 추가하려면 보고서 디자인 뷰에서 보고서 작성기를 엽니다. 마법사나 보고서 데이터 창에서 보고서 서버로 이동하고 보고서에 추가할 공유 데이터 세트를 선택합니다. 이 뷰에서는 필드를 추가하는 것을 제외하고는 쿼리를 변경할 수 없습니다. 다른 데이터 옵션을 무시하고 필터를 추가할 수도 있지만 필터를 제거할 수는 없습니다.  
  
3.  다음 표에서는 보고서 서버의 공유 데이터 세트 정의에 대해 구성할 수 있는 속성과 보고서 정의의 공유 데이터 세트 인스턴스에 대해 구성할 수 있는 속성을 비교합니다.  
  
    |속성|정의에 대한 구성 정보|인스턴스에 대한 구성 정보|  
    |--------------|--------------------------------------------|------------------------------------------|  
    |쿼리 텍스트|쿼리 구성(쿼리를 식으로 정의하는 작업 포함)|쿼리를 변경할 수 없음|  
    |쿼리 매개 변수|보고서 매개 변수를 참조할 수 없음<br /><br /> 기본값을 포함함<br /><br /> 읽기 전용 플래그를 포함함|정의에서 읽기 전용으로 표시되지 않은 매개 변수 구성|  
    |필터|필터 정의|정의의 일부인 데이터 세트 필터를 보거나 변경할 수 없음<br /><br /> 추가 필터를 만들 수 없음|  
    |데이터 원본|공유 데이터 원본이어야 함|공유 데이터 원본을 변경할 수 없음|  
    |필드|쿼리 명령의 필드<br /><br /> 데이터 세트 정의의 일부가 아닌 계산 필드|필드를 볼 수 있지만 변경할 수는 없음<br /><br /> 필드 컬렉션은 보고서에 공유 데이터 세트를 추가할 때의 쿼리를 기반으로 정적입니다. 업데이트하려면 **데이터 세트 속성** 대화 상자에서 **필드 새로 고침**을 클릭합니다. 실제 필드 컬렉션은 정의의 현재 쿼리가 반환하는 필드 컬렉션입니다.<br /><br /> 계산 필드 추가|  
    |데이터 세트|대/소문자 구분과 같은 데이터 옵션|인스턴스의 데이터 옵션 무시|  
  
## <a name="embedded-datasets"></a>포함된 데이터 세트  
 외부 데이터 원본에서 하나의 보고서에서만 사용할 데이터를 가져오려는 경우 포함된 데이터 세트를 사용합니다. 포함된 데이터 세트는 다른 종속성이 없고 여러 보고서에 사용할 필요가 없는 쿼리를 만들려는 경우에 유용합니다.  
  
 포함된 데이터 세트를 만들거나 편집하려면 보고서 데이터 창을 사용합니다. 데이터 세트를 만든 후에 **데이터 세트 속성** 대화 상자에서 속성을 구성할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [포함 된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본 &#40;보고서 작성기 및 SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [공유 데이터 집합 또는 포함 된 데이터 집합 &#40;보고서 작성기 및 SSRS를 만듭니다&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-datasets-ssrs.md)   
 [데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [보고서 서비스의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  