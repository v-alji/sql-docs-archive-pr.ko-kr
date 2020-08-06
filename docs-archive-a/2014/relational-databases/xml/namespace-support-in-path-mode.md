---
title: PATH 모드에서의 네임스페이스 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: rothja
ms.author: jroth
ms.openlocfilehash: abd6cd1f5590bffcd841b07897c9685faed4726f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729152"
---
# <a name="namespace-support-in-path-mode"></a><span data-ttu-id="f81c4-102">PATH 모드에서의 네임스페이스 지원</span><span class="sxs-lookup"><span data-stu-id="f81c4-102">Namespace Support in PATH Mode</span></span>
  <span data-ttu-id="f81c4-103">WITH NAMESPACES를 사용하여 PATH 모드에 네임스페이스 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f81c4-103">Namespace support in the PATH mode is provided by using WITH NAMESPACES.</span></span> <span data-ttu-id="f81c4-104">예를 들어 다음 쿼리에서는 후속 SELECT 문에 사용할 수 있는 네임스페이스("a:")를 선언할 WITH NAMESPACES 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f81c4-104">For example, the following query demonstrates the WITH NAMESPACES syntax to declare a namespace ("a:") that can then be used in the subsequent SELECT statement:</span></span>  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a><span data-ttu-id="f81c4-105">예제</span><span class="sxs-lookup"><span data-stu-id="f81c4-105">Examples</span></span>  
 <span data-ttu-id="f81c4-106">다음 예제에서는 SELECT 쿼리에서 XML을 생성할 때 PATH 모드를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f81c4-106">These samples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="f81c4-107">이러한 쿼리는 대부분 ProductModel 테이블의 Instructions 열에 저장된 자전거 제조 지침 XML 문서에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f81c4-107">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81c4-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f81c4-108">See Also</span></span>  
 [<span data-ttu-id="f81c4-109">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="f81c4-109">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
