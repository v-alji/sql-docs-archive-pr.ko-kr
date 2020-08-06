---
title: IOpenRowset을 사용하여 행 집합 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739813"
---
# <a name="creating-a-rowset-with-iopenrowset"></a><span data-ttu-id="ab268-102">IOpenRowset을 사용하여 행 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="ab268-102">Creating a Rowset with IOpenRowset</span></span>
  <span data-ttu-id="ab268-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같은 제한 사항이 있는 **iopenrowset:: OpenRowset** 메서드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IOpenRowset::OpenRowset** method with the following restrictions:</span></span>  
  
-   <span data-ttu-id="ab268-104">데이터베이스 ID(DBID) 구조체에 *pTableID* 매개 변수가 가리키는 기본 테이블 또는 뷰를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-104">A base table or view must be specified in a database ID (DBID) structure that the *pTableID* parameter points to.</span></span>  
  
-   <span data-ttu-id="ab268-105">DBID *eKind* 멤버는 DBKIND_NAME을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-105">The DBID *eKind* member must indicate DBKIND_NAME.</span></span>  
  
-   <span data-ttu-id="ab268-106">DBID *uName* 멤버는 기존의 기본 테이블 또는 뷰 이름을 유니코드 문자열로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-106">The DBID *uName* member must specify the name of an existing base table or a view as a Unicode character string.</span></span>  
  
-   <span data-ttu-id="ab268-107">**OpenRowset**의 *pIndexID* 매개 변수는 NULL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-107">The *pIndexID* parameter of **OpenRowset** must be NULL.</span></span>  
  
 <span data-ttu-id="ab268-108">**IOpenRowset::OpenRowset**의 결과 집합에는 단일 행 집합이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-108">The result set of **IOpenRowset::OpenRowset** contains a single rowset.</span></span> <span data-ttu-id="ab268-109">단일 행 집합을 포함 하는 결과 집합은 커서에서 지원 될 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ab268-109">Result sets that contain a single rowset can be supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.</span></span> <span data-ttu-id="ab268-110">커서 지원을 통해 개발자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 동시성 메커니즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab268-110">Cursor support allows the developer to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab268-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab268-111">See Also</span></span>  
 [<span data-ttu-id="ab268-112">행 집합</span><span class="sxs-lookup"><span data-stu-id="ab268-112">Rowsets</span></span>](rowsets.md)  
  
  
