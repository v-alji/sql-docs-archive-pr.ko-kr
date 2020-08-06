---
title: FILESTREAM 지원 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
ms.openlocfilehash: cde3c2cd1b72773cfcf17eacedeb3276dd2f63da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652788"
---
# <a name="filestream-support-ole-db"></a><span data-ttu-id="751ac-102">FILESTREAM 지원(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="751ac-102">FILESTREAM Support (OLE DB)</span></span>
  <span data-ttu-id="751ac-103">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0부터 OLE DB는 향상 된 FILESTREAM 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-103">Beginning with [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB supports the enhanced FILESTREAM feature.</span></span> <span data-ttu-id="751ac-104">이 기능에 대 한 자세한 내용은 [FILESTREAM 지원](../features/filestream-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="751ac-104">For more information about this feature, see [FILESTREAM Support](../features/filestream-support.md).</span></span> <span data-ttu-id="751ac-105">샘플은 [Filestream 및 OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="751ac-105">For samples, see [Filestream and OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).</span></span>  
  
 <span data-ttu-id="751ac-106">2GB보다 큰 `varbinary(max)` 값을 보내고 받기 위해 애플리케이션에서는 매개 변수와 결과 바인딩에 `DBTYPE_IUNKNOWN`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-106">To send and receive `varbinary(max)` values greater than 2 GB, an application uses `DBTYPE_IUNKNOWN` in parameter and result bindings.</span></span> <span data-ttu-id="751ac-107">매개 변수의 경우 공급자는 ISequentialStream 및 ISequentialStream을 반환하는 결과에 대해 IUnknown::QueryInterface를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-107">For parameters the provider must call IUnknown::QueryInterface for ISequentialStream and for results that return ISequentialStream.</span></span>  
  
 <span data-ttu-id="751ac-108">OLE DB의 경우 ISequentialStream 값과 관련된 검사가 완화될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-108">For OLE DB, checking related to ISequentialStream values will be relaxed.</span></span> <span data-ttu-id="751ac-109">*Wtype* 이 `DBTYPE_IUNKNOWN` 구조체에 있는 경우 `DBBINDING` `DBPART_LENGTH` *dwpart* 에서 생략 하거나 데이터의 길이 (데이터 버퍼의 오프셋 *oblength* )를 ~ 0으로 설정 하 여 길이 검사를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-109">When *wType* is `DBTYPE_IUNKNOWN` in the `DBBINDING` struct, length checking can be disabled either by omitting `DBPART_LENGTH` from *dwPart* or by setting the length of the data (at offset *obLength* in the data buffer) to ~0.</span></span> <span data-ttu-id="751ac-110">이렇게 하면 공급자는 값의 길이를 검사하지 않고 스트림을 통해 사용할 수 있는 모든 데이터를 요청하고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-110">In this case, the provider will not check the length of the value and will request and return all of the data available through the stream.</span></span> <span data-ttu-id="751ac-111">이러한 변경 사항은 모든 LOB(큰 개체) 형식과 XML에 적용되지만, 이는 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상의 서버에 연결된 경우에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-111">This change will be applied to all large object (LOB) types and XML, but only when connected to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (or later) servers.</span></span> <span data-ttu-id="751ac-112">이 기능은 개발자에게 더 나은 융통성을 제공할 뿐만 아니라 기존 애플리케이션 및 하위 서버를 위한 일관성과 이전 버전과의 호환성을 유지할 수 있게 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-112">This will provide greater flexibility for developers, while maintaining consistency and backwards compatibility for existing applications and downlevel servers.</span></span>  
  
 <span data-ttu-id="751ac-113">이 변경 내용은 데이터를 전송하는 모든 인터페이스(주로 IRowset::GetData, ICommand::Execute, IRowsetFastLoad::InsertRow)에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="751ac-113">This change affects all interfaces that transfer data, principally IRowset::GetData, ICommand::Execute, and IRowsetFastLoad::InsertRow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751ac-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="751ac-114">See Also</span></span>  
 [<span data-ttu-id="751ac-115">SQL Server Native Client 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="751ac-115">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
