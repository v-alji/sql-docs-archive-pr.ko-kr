---
title: XSINIL 매개 변수를 사용하여 NULL 값 요소 생성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 602de12b5aa9be8997fbd49a2f23e0b73444aac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743063"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a><span data-ttu-id="0616d-102">XSINIL 매개 변수를 사용하여 NULL 값 요소 생성</span><span class="sxs-lookup"><span data-stu-id="0616d-102">Generate Elements for NULL Values with the XSINIL Parameter</span></span>
  <span data-ttu-id="0616d-103">**ELEMENTS** 지시어는 각 열 값이 XML의 요소로 매핑되는 XML을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0616d-103">The **ELEMENTS** directive constructs XML in which each column value maps to an element in the XML.</span></span> <span data-ttu-id="0616d-104">열 값이 NULL이면 요소가 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0616d-104">If the column value is NULL, no element is added.</span></span> <span data-ttu-id="0616d-105">ELEMENTS 지시어에 선택 항목인 **XSINIL** 매개 변수를 지정하면 NULL 값에 대해서도 요소가 생성되도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0616d-105">By specifying the optional **XSINIL** parameter on the ELEMENTS directive, you can request that an element also be created for the NULL value.</span></span> <span data-ttu-id="0616d-106">이 경우 **xsi:nil** 특성이 TRUE로 설정된 요소가 각 NULL 열 값에 대해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0616d-106">In this case, an element that has the **xsi:nil** attribute set to TRUE is returned for each NULL column value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0616d-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0616d-107">See Also</span></span>  
 [<span data-ttu-id="0616d-108">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="0616d-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
