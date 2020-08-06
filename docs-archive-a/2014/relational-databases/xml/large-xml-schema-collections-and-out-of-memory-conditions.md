---
title: 대형 XML 스키마 컬렉션 및 메모리 부족 상태 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743048"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a><span data-ttu-id="19e8b-102">대형 XML 스키마 컬렉션 및 메모리 부족 상태</span><span class="sxs-lookup"><span data-stu-id="19e8b-102">Large XML Schema Collections and Out-of-Memory Conditions</span></span>
  <span data-ttu-id="19e8b-103">대형 XML 스키마 컬렉션에서 기본 제공 XML_SCHEMA_NAMESPACE() 함수를 호출하거나 대형 XML 스키마 컬렉션을 삭제하려고 하면 메모리가 부족해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-103">During a call to the built-in XML_SCHEMA_NAMESPACE() function on a large XML schema collection, or when you try to drop large XML schema collections, an out-of-memory condition may occur.</span></span> <span data-ttu-id="19e8b-104">이러한 문제를 처리할 수 있는 해결책은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-104">The following are solutions you can use to handle this:</span></span>  
  
-   <span data-ttu-id="19e8b-105">시스템 로드가 많지 않은 경우 DROP_XML_SCHEMA_COLLECTION 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-105">When the system load is light, use the DROP_XML_SCHEMA_COLLECTION command.</span></span> <span data-ttu-id="19e8b-106">이 명령이 실패하면 ALTER DATABASE 문을 사용하고 DROP XML SCHEMA COLLECTION을 다시 시도하여 데이터베이스를 단일 사용자 모드로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-106">If this fails, put the database in single-user mode by using the ALTER DATABASE statement and trying DROP XML SCHEMA COLLECTION again.</span></span> <span data-ttu-id="19e8b-107">해당 XML 스키마 컬렉션이 **master**, **model**또는 **tempdb**에 있을 경우 단일 사용자 모드로 설정하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-107">If the XML schema collection exists in **master**, **model**, or **tempdb**, a server restart is required for single-user mode.</span></span>  
  
-   <span data-ttu-id="19e8b-108">XML_SCHEMA_NAMESPACE를 호출할 경우 하나의 XML 스키마 네임스페이스만 검색하거나 시스템 로드가 더 적을 때 호출을 시도하거나 단일 사용자 모드로 호출을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19e8b-108">When you call the XML_SCHEMA_NAMESPACE, you can try to retrieve a single XML schema namespace, you can try the call when the system load is lighter, or you can try the call in single-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e8b-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19e8b-109">See Also</span></span>  
 [<span data-ttu-id="19e8b-110">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="19e8b-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
