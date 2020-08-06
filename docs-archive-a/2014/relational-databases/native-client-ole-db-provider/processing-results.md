---
title: 결과 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: rothja
ms.author: jroth
ms.openlocfilehash: b9e5bf00b4d2e554536c9f2ba1a328390b93a8a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653827"
---
# <a name="processing-results"></a><span data-ttu-id="406bd-102">결과 처리</span><span class="sxs-lookup"><span data-stu-id="406bd-102">Processing Results</span></span>
  <span data-ttu-id="406bd-103">명령을 실행하거나 공급자에서 직접 행 집합 개체를 생성하여 행 집합 개체가 만들어진 경우 소비자가 행 집합의 데이터를 검색하여 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-103">If a rowset object is produced by either the execution of a command or the generation of a rowset object directly from the provider, the consumer needs to retrieve and access data in the rowset.</span></span>  
  
 <span data-ttu-id="406bd-104">행 집합은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 데이터를 테이블 형식으로 노출할 수 있도록 하는 중앙 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-104">Rowsets are the central objects that enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to expose data in tabular form.</span></span> <span data-ttu-id="406bd-105">개념상, 행 집합은 각 행이 열 데이터를 갖는 행의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-105">Conceptually, a rowset is a set of rows in which each row has column data.</span></span> <span data-ttu-id="406bd-106">행 집합 개체는 **IRowset**(행 집합에서 순차적으로 행을 인출하기 위한 메서드 포함), **IAccessor**(테이블 형식 데이터가 소비자 프로그램 변수에 바인딩되는 방법을 설명하는 열 바인딩 그룹의 정의 허용), **IColumnsInfo**(행 집합의 열에 대한 정보 제공) 및 **IRowsetInfo**(행 집합에 대한 정보 제공)와 같은 인터페이스를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-106">A rowset object exposes interfaces such as **IRowset** (contains methods for fetching rows from the rowset sequentially), **IAccessor** (permits the definition of a group of column bindings describing the way tabular data is bound to consumer program variables), **IColumnsInfo** (provides information about columns in the rowset), and **IRowsetInfo** (provides information about rowset).</span></span>  
  
 <span data-ttu-id="406bd-107">소비자는 **IRowset::GetData** 메서드를 호출하여 행 집합의 데이터 행을 버퍼로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-107">A consumer can call the **IRowset::GetData** method to retrieve a row of data from the rowset into a buffer.</span></span> <span data-ttu-id="406bd-108">**GetData**를 호출하기 전에 소비자는 DBBINDING 구조 집합을 사용하여 버퍼를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-108">Before **GetData** is called, the consumer describes the buffer using a set of DBBINDING structures.</span></span> <span data-ttu-id="406bd-109">각 바인딩은 행 집합이 소비자 버퍼에 저장되는 방법을 설명하며 다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-109">Each binding describes how a column in a rowset is stored in a consumer buffer and contains the following:</span></span>  
  
-   <span data-ttu-id="406bd-110">바인딩이 적용되는 열(또는 매개 변수)의 서수</span><span class="sxs-lookup"><span data-stu-id="406bd-110">Ordinal of the column (or parameter) to which the binding applies.</span></span>  
  
-   <span data-ttu-id="406bd-111">바인딩되는 항목에 대한 정보(예: 데이터 값, 데이터 길이 및 바인딩 상태)</span><span class="sxs-lookup"><span data-stu-id="406bd-111">Information about what is bound (for example, data value, length of the data, and its binding status).</span></span>  
  
-   <span data-ttu-id="406bd-112">이러한 각 부분에 대한 버퍼의 오프셋 정보</span><span class="sxs-lookup"><span data-stu-id="406bd-112">Information about what is offset in the buffer to each of these parts.</span></span>  
  
-   <span data-ttu-id="406bd-113">소비자 버퍼에 존재하는 데이터 값의 길이와 유형</span><span class="sxs-lookup"><span data-stu-id="406bd-113">Length and type of the data values as they exist in the consumer buffer.</span></span>  
  
 <span data-ttu-id="406bd-114">데이터를 가져올 때 공급자는 각 바인딩의 정보를 사용하여 소비자 버퍼에서 데이터를 검색하는 위치와 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-114">When getting the data, the provider uses information in each binding to determine where and how to retrieve data from the consumer buffer.</span></span> <span data-ttu-id="406bd-115">소비자 버퍼에 데이터를 설정하는 경우에는 각 바인딩의 정보를 사용하여 데이터를 소비자 버퍼에 반환하는 위치와 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-115">When setting data in the consumer buffer, the provider uses information in each binding to determine where and how to return data in the consumer's buffer.</span></span>  
  
 <span data-ttu-id="406bd-116">DBBINDING 구조가 지정된 후 접근자가 생성됩니다(**IAccessor::CreateAccessor**).</span><span class="sxs-lookup"><span data-stu-id="406bd-116">After the DBBINDING structures are specified, an accessor is created (**IAccessor::CreateAccessor**).</span></span> <span data-ttu-id="406bd-117">접근자는 바인딩 컬렉션으로, 소비자 버퍼의 데이터를 가져오거나 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="406bd-117">An accessor is a collection of bindings and is used to get or set the data in the consumer buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406bd-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="406bd-118">See Also</span></span>  
 <span data-ttu-id="406bd-119">[SQL Server Native Client OLE DB 공급자 응용 프로그램 만들기](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="406bd-119">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="406bd-120">OLE DB 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="406bd-120">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
