---
title: ISSAbort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7195311fefe3f0f1b7b4d6d789aa8d8487bc3bfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742487"
---
# <a name="issabort-ole-db"></a><span data-ttu-id="9790b-102">ISSAbort(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="9790b-102">ISSAbort (OLE DB)</span></span>
  <span data-ttu-id="9790b-103">Native Client OLE DB 공급자에 노출 되는 **ISSAbort** 인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 현재 행 집합을 취소 하는 데 사용 되는 [ISSAbort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) 메서드와, 처음에 행 집합을 생성 한 명령을 사용 하 여 일괄 처리 되 고 아직 실행이 완료 되지 않은 모든 명령을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9790b-103">The **ISSAbort** interface, which is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, provides the [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) method that is used to cancel the current rowset plus any commands batched with the command that initially generated the rowset, and that have not yet completed execution.</span></span>  
  
 <span data-ttu-id="9790b-104">**ISSAbort** 은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ICommand:: Execute** 또는 **iopenrowset:: OpenRowset**에서 반환 된 **IMultipleResults** 개체에 대해 **QueryInterface** 를 사용 하 여 사용할 수 있는 Native Client 공급자별 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9790b-104">**ISSAbort** is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider-specific interface available by using **QueryInterface** on the **IMultipleResults** object returned by **ICommand::Execute** or **IOpenRowset::OpenRowset**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9790b-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9790b-105">In This Section</span></span>  
  
|<span data-ttu-id="9790b-106">메서드</span><span class="sxs-lookup"><span data-stu-id="9790b-106">Method</span></span>|<span data-ttu-id="9790b-107">설명</span><span class="sxs-lookup"><span data-stu-id="9790b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9790b-108">ISSAbort:: Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9790b-108">ISSAbort::Abort &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|<span data-ttu-id="9790b-109">현재 행 집합 및 현재 명령과 연결된 일괄 처리되는 명령을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9790b-109">Cancels the current rowset plus any batched commands associated with the current command.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9790b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9790b-110">See Also</span></span>  
 [<span data-ttu-id="9790b-111">인터페이스&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9790b-111">Interfaces &#40;OLE DB&#41;</span></span>](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
