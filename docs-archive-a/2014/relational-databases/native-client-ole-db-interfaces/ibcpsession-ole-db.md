---
title: IBCPSession(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d32da9c06a200d5924dbae18d6b7513f46c88ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739808"
---
# <a name="ibcpsession-ole-db"></a><span data-ttu-id="ca654-102">IBCPSession(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ca654-102">IBCPSession (OLE DB)</span></span>
  <span data-ttu-id="ca654-103">**IBCPSession** 인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 파일 기반 대량 복사 작업에 대한 지원을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-103">The **IBCPSession** interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file-based bulk copy operations.</span></span> <span data-ttu-id="ca654-104">**IBCPSession** 인터페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자에서 세션과 같은 수준에 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-104">The **IBCPSession** interface is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider under the same level as Sessions.</span></span> <span data-ttu-id="ca654-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자에서 데이터 원본 개체는 세션 개체에 대한 팩터리이고 대량 복사 작업은 연결 속성 SSPROP_ENABLEBULKCOPY에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-105">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, data source objects are factories for Session objects, and bulk copy operations are specified in the connection property SSPROP_ENABLEBULKCOPY.</span></span> <span data-ttu-id="ca654-106">또한 SSPROP_ENABLEFASTLOAD 속성을 true로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-106">In addition, the SSPROP_ENABLEFASTLOAD property should be set to true.</span></span>  
  
 <span data-ttu-id="ca654-107">그런 다음 **IDBCreateSession::CreateSession** 메서드를 호출하면 **BulkCopySession** 개체가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-107">Calling the **IDBCreateSession::CreateSession** method will then result in the creation of a **BulkCopySession** object.</span></span> <span data-ttu-id="ca654-108">그러면 **IBCPSession** 개체를 통해 노출되는 모든 파일 기반 대량 복사 메서드를 이 **IBCPSession** 개체의 **IBCPSession** 인터페이스에서 거의 유사한 서명을 사용하여 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-108">All the file-based bulk copy methods exposed through the **IBCPSession** object are then callable with nearly similar signatures on this **IBCPSession** object's **IBCPSession** interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca654-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 [IRowsetFastLoad](irowsetfastload-ole-db.md) 인터페이스를 통해 메모리 기반 대량 복사 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports memory-based bulk copy operations through the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="ca654-110">대량 복사 작업에 Native Client OLE DB 공급자를 사용 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [대량 복사 작업 수행](../native-client/features/performing-bulk-copy-operations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca654-110">For more information about using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider for bulk copy operations, see [Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="ca654-111">**IBCPSession** 인터페이스를 사용하는 방법을 보여주는 샘플은 [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca654-111">For a sample showing how to use the **IBCPSession** interface, see [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca654-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ca654-112">In This Section</span></span>  
  
|<span data-ttu-id="ca654-113">메서드</span><span class="sxs-lookup"><span data-stu-id="ca654-113">Method</span></span>|<span data-ttu-id="ca654-114">설명</span><span class="sxs-lookup"><span data-stu-id="ca654-114">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca654-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolfmt-ole-db.md)|<span data-ttu-id="ca654-116">프로그램 변수와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 간의 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-116">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>|  
|[<span data-ttu-id="ca654-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolumns-ole-db.md)|<span data-ttu-id="ca654-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 열에 바인딩될 필드의 개수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-118">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="ca654-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcontrol-ole-db.md)|<span data-ttu-id="ca654-120">대량 복사 작업에 대한 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-120">Sets the options for a bulk copy operation.</span></span>|  
|[<span data-ttu-id="ca654-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span></span>](ibcpsession-bcpdone-ole-db.md)|<span data-ttu-id="ca654-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 보낼 나머지 행을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-122">Commits the remaining rows to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="ca654-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span></span>](ibcpsession-bcpexec-ole-db.md)|<span data-ttu-id="ca654-124">대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-124">Performs the bulk copy operation.</span></span>|  
|[<span data-ttu-id="ca654-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span></span>](ibcpsession-bcpinit-ole-db.md)|<span data-ttu-id="ca654-126">대량 복사 구조를 초기화하고, 일부 오류 검사를 수행하고, 데이터 및 서식 파일 이름이 올바른지 확인한 다음 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-126">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>|  
|[<span data-ttu-id="ca654-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpreadfmt-ole-db.md)|<span data-ttu-id="ca654-128">서식 파일에서 각 열의 서식 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-128">Reads format information for each column from the format file.</span></span>|  
|[<span data-ttu-id="ca654-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpwritefmt-ole-db.md)|<span data-ttu-id="ca654-130">각 열에 대한 서식 정보를 서식 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="ca654-130">Writes format information for each column to the format file.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca654-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca654-131">See Also</span></span>  
 [<span data-ttu-id="ca654-132">인터페이스&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca654-132">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
