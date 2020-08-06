---
title: ISQLServerErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISQLServerErrorInfo interface
ms.assetid: a8323b5c-686a-4235-a8d2-bda43617b3a1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 222349bcaa88058dea1d9c5302883667c22d4092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742492"
---
# <a name="isqlservererrorinfo-ole-db"></a><span data-ttu-id="a9e77-102">ISQLServerErrorInfo(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a9e77-102">ISQLServerErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="a9e77-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 **ISQLServerErrorInfo** 오류 인터페이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e77-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the **ISQLServerErrorInfo** error interface.</span></span> <span data-ttu-id="a9e77-104">이 인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류의 심각도 및 상태를 비롯하여 오류에 대한 자세한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e77-104">This interface returns details from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error, including its severity and state.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9e77-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a9e77-105">In This Section</span></span>  
  
|<span data-ttu-id="a9e77-106">메서드</span><span class="sxs-lookup"><span data-stu-id="a9e77-106">Method</span></span>|<span data-ttu-id="a9e77-107">설명</span><span class="sxs-lookup"><span data-stu-id="a9e77-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9e77-108">ISQLServerErrorInfo:: GetErrorInfo &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a9e77-108">ISQLServerErrorInfo::GetErrorInfo &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)|<span data-ttu-id="a9e77-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 정보가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자의 SSERRORINFO 구조에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e77-109">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9e77-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9e77-110">See Also</span></span>  
 <span data-ttu-id="a9e77-111">[인터페이스 &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="a9e77-111">[Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="a9e77-112">SQL Server 오류 세부 정보</span><span class="sxs-lookup"><span data-stu-id="a9e77-112">SQL Server Error Detail</span></span>](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
  
