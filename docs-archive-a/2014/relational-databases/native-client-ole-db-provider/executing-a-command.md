---
title: 명령 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e8da036d5a4b6469a31213247ad7d4edb7dbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653828"
---
# <a name="executing-a-command"></a><span data-ttu-id="1292b-102">명령 실행</span><span class="sxs-lookup"><span data-stu-id="1292b-102">Executing a Command</span></span>
  <span data-ttu-id="1292b-103">데이터 원본에 대한 연결이 설정된 후 소비자는 **IDBCreateSession::CreateSession** 메서드를 호출하여 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-103">After the connection to a data source is established, the consumer calls the **IDBCreateSession::CreateSession** method to create a session.</span></span> <span data-ttu-id="1292b-104">세션은 명령, 행 집합 또는 트랜잭션 팩토리로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-104">The session acts as a command, rowset, or transaction factory.</span></span>  
  
 <span data-ttu-id="1292b-105">개별 테이블이나 인덱스를 직접 사용하기 위해 소비자는 `IOpenRowset` 인터페이스를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-105">To work directly with individual tables or indexes, the consumer requests the `IOpenRowset` interface.</span></span> <span data-ttu-id="1292b-106">`IOpenRowset::OpenRowset` 메서드는 단일 기본 테이블이나 인덱스의 모든 행이 포함된 행 집합을 열고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-106">The `IOpenRowset::OpenRowset` method opens and returns a rowset that includes all rows from a single base table or index.</span></span>  
  
 <span data-ttu-id="1292b-107">명령을 실행 하기 위해 (예: \* Authors에서 선택) 소비자는 인터페이스를 요청 `IDBCreateCommand` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-107">To execute a command (such as SELECT \* FROM Authors), the consumer requests the `IDBCreateCommand` interface.</span></span> <span data-ttu-id="1292b-108">소비자는 `IDBCreateCommand::CreateCommand` 메서드를 호출하여 명령 개체를 만들고 `ICommandText` 인터페이스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-108">The consumer can execute the `IDBCreateCommand::CreateCommand` method to create a command object and request for the `ICommandText` interface.</span></span> <span data-ttu-id="1292b-109">실행할 명령을 지정하는 데는 `ICommandText::SetCommandText` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-109">The `ICommandText::SetCommandText` method is used to specify the command that is to be executed.</span></span>  
  
 <span data-ttu-id="1292b-110">명령을 실행하는 데는 `Execute` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-110">The `Execute` command is used to execute the command.</span></span> <span data-ttu-id="1292b-111">SQL 문이나 프로시저 이름은 모두 명령으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-111">The command can be any SQL statement or procedure name.</span></span> <span data-ttu-id="1292b-112">결과 집합(행 집합) 개체를 생성하지 않는 명령도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-112">Not all commands produce a result set (rowset) object.</span></span> <span data-ttu-id="1292b-113">SELECT \* FROM Authors와 같은 명령은 결과 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1292b-113">Commands such as SELECT \* FROM Authors produce a result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1292b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1292b-114">See Also</span></span>  
 [<span data-ttu-id="1292b-115">SQL Server Native Client OLE DB 공급자 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="1292b-115">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
