---
title: UDT(사용자 정의 데이터 형식)에 대한 FOR XML 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: rothja
ms.author: jroth
ms.openlocfilehash: b668ad2da13fdfc880ab26cb2b2759ff3693f7d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743087"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a><span data-ttu-id="6fd0f-102">사용자 정의 데이터 형식(UDT)에 대한 FOR XML 지원</span><span class="sxs-lookup"><span data-stu-id="6fd0f-102">FOR XML Support for the User-Defined Data Types (UDT)</span></span>
  <span data-ttu-id="6fd0f-103">FOR XML은 CLR(공용 언어 런타임) UDT(사용자 정의 데이터 형식)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fd0f-103">FOR XML does not support common language runtime (CLR) user-defined data types (UDTs).</span></span>  
  
 <span data-ttu-id="6fd0f-104">CLR 사용자 정의 데이터 형식으로 FOR XML을 사용하려면 데이터 형식에 XML 직렬화가 있는지 확인하고 FOR XML 선택 절의 XML로의 명시적 캐스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6fd0f-104">To use FOR XML with CLR user-defined data types, make sure that the data type has an XML serialization, and use an explicit cast to XML in the FOR XML select clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd0f-105">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6fd0f-105">See Also</span></span>  
 [<span data-ttu-id="6fd0f-106">다양한 SQL Server 데이터 형식에 대한 FOR XML 지원</span><span class="sxs-lookup"><span data-stu-id="6fd0f-106">FOR XML Support for Various SQL Server Data Types</span></span>](for-xml-support-for-various-sql-server-data-types.md)  
  
  
