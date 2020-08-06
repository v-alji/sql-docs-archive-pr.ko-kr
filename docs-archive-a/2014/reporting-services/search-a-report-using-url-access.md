---
title: URL 액세스를 사용하여 보고서 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b45f3fabf58a0980d41ee7b4b89a771655477d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739190"
---
# <a name="search-a-report-using-url-access"></a><span data-ttu-id="95852-102">URL 액세스를 사용하여 보고서 검색</span><span class="sxs-lookup"><span data-stu-id="95852-102">Search a Report Using URL Access</span></span>
  <span data-ttu-id="95852-103">URL 액세스를 사용하여 특정 텍스트 집합에 대한 보고서를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95852-103">You can search a report for a specific set of text using URL access.</span></span> <span data-ttu-id="95852-104">보고서를 검색하려면 URL의 *rc:FindString* 매개 변수 값을 검색할 텍스트에 해당하는 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95852-104">To search a report, set the value of the *rc:FindString* parameter on the URL equal to the text for which you want to search.</span></span> <span data-ttu-id="95852-105">아울러 *rc:StartFind* 및 *rc:EndFind* 매개 변수를 사용하여 보고서 내의 특정 페이지로 검색 범위를 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95852-105">Additionally, use the *rc:StartFind* and *rc:EndFind* parameters to narrow your search to specific pages within the report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95852-106">예제</span><span class="sxs-lookup"><span data-stu-id="95852-106">Example</span></span>  
 <span data-ttu-id="95852-107">다음 URL 액세스 예제는 Product Catalog 예제 보고서에서 1~5페이지 중 처음 나타나는 "Mountain-400" 텍스트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="95852-107">The following URL access example searches for the first occurrence of the text "Mountain-400" in the Product Catalog sample report starting with page one and ending with page five:</span></span>  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a><span data-ttu-id="95852-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95852-108">See Also</span></span>  
 <span data-ttu-id="95852-109">[URL 액세스&#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="95852-109">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="95852-110">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="95852-110">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
