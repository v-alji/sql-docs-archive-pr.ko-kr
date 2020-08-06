---
title: CLR에서 LOB (Large Object) 매개 변수 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742276"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a><span data-ttu-id="3fd11-102">CLR의 LOB(Large Object) 매개 변수 처리</span><span class="sxs-lookup"><span data-stu-id="3fd11-102">Handling Large Object (LOB) Parameters in the CLR</span></span>
  <span data-ttu-id="3fd11-103">LOB(Large Object) 이진 형식(`SqlBytes`) 및 LOB 문자 형식(`SqlChars`) 매개 변수는 각각 `varbinary(max)`와 `nvarchar(max)`를 사용하여 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="3fd11-103">Use `SqlBytes` and `SqlChars` to pass large object (LOB) binary type (`varbinary(max)`) and LOB character type (`nvarchar(max)`) parameters, respectively.</span></span> <span data-ttu-id="3fd11-104">이러한 형식을 사용하면 값 전체를 관리되는 공간에 복사하는 대신 데이터베이스의 LOB 값을 CLR(공용 언어 런타임) 루틴에 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fd11-104">These types allow streaming the LOB values from the database to the common language runtime (CLR) routine, instead of copying the entire value into managed space.</span></span> <span data-ttu-id="3fd11-105">`SqlBinary` 및 `SqlString`은 작은 이진 및 문자열 값에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fd11-105">`SqlBinary` and `SqlString` should be used only for small binary and character string values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd11-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3fd11-106">See Also</span></span>  
 [<span data-ttu-id="3fd11-107">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3fd11-107">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
