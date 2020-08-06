---
title: ICommand(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: rothja
ms.author: jroth
ms.openlocfilehash: 03bdccc83a04078210f2283d0b330f237ed02979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659961"
---
# <a name="icommand-ole-db"></a><span data-ttu-id="526af-102">ICommand(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="526af-102">ICommand (OLE DB)</span></span>
  <span data-ttu-id="526af-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client의 고유한 OLE DB 동작을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="526af-103">This topic discusses OLE DB behavior that is specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="icommandexecute"></a><span data-ttu-id="526af-104">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="526af-104">ICommand::Execute</span></span>  
 <span data-ttu-id="526af-105">열 크기보다 큰 데이터를 삽입하면 일반적으로 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="526af-105">Inserting data that is greater than the size of a column typically results in an error.</span></span> <span data-ttu-id="526af-106">그러나 경우에 따라서는 S_OK가 반환되는 상황에서 *dwStatus* 가 DBSTATUS_S_TRUNCATED로 설정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="526af-106">However, there are situations where S_OK will be returned but the *dwStatus* will be set to DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="526af-107">이 문제는 대개 매개 변수를 사용하여 데이터를 삽입할 때 열이 너무 작아 데이터를 저장할 수 없고 `ICommandWithParameters::SetParameterInfo`가 호출되지 않은 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="526af-107">This generally occurs when inserting data with parameters, where the column is not large enough to hold the data, and `ICommandWithParameters::SetParameterInfo` has not been called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526af-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="526af-108">See Also</span></span>  
 [<span data-ttu-id="526af-109">인터페이스&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="526af-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
