---
title: 대량 로드 보안 고려 사항 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- bulk load [SQLXML], security
- security [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], security
ms.assetid: 192fc6d4-ecbc-4a4d-a5cb-55e1f64af318
author: rothja
ms.author: jroth
ms.openlocfilehash: 21c1cbe7f94ef42327aa7b81f75fa521d9f7c0e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661636"
---
# <a name="bulk-load-security-considerations-sqlxml-40"></a><span data-ttu-id="8b932-102">대량 로드 보안 고려 사항(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8b932-102">Bulk Load Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="8b932-103">다음은 XML 대량 로드를 사용하기 위한 보안 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-103">The following are security guidelines for using XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="8b932-104">대량 로드 작업을 트랜잭션으로 수행하도록 지정하는 경우 `TempFilePath` 속성을 사용하여 임시 파일을 만들 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-104">When you specify that the Bulk Load operation is to be performed as a transaction, you use the `TempFilePath` property to specify a folder in which to create the temporary files.</span></span>  
  
     <span data-ttu-id="8b932-105">대량 로드 프로세스에서는 이러한 임시 파일을 다음과 같은 사용 권한으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-105">The Bulk Load process creates these temporary files with the following permissions:</span></span>  
  
    -   <span data-ttu-id="8b932-106">읽기/쓰기/삭제 액세스 권한이 대량 로드 프로세스에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-106">Read/Write/Delete access is granted to the Bulk Load process.</span></span>  
  
    -   <span data-ttu-id="8b932-107">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 이러한 파일에 액세스하는 데 사용할 계정을 알 수 없으므로 모든 사용자에게 읽기 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-107">Read permission is granted to all users, because the account under which Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will access these files is unknown.</span></span> <span data-ttu-id="8b932-108">이러한 임시 파일이 포함된 폴더에 대해 적절한 사용 권한을 설정하여 이 파일에 대한 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-108">You can restrict the access to these temporary files by setting the appropriate permissions on the folder that contains them.</span></span>  
  
-   <span data-ttu-id="8b932-109">XML 대량 로드 자체에는 사용 권한 설정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-109">XML Bulk Load does not itself have any permissions settings.</span></span> <span data-ttu-id="8b932-110">대량 로드에서는 데이터베이스가 올바로 설정되어 있고 사용자 컨텍스트(즉, 대량 로드에 사용하도록 설정된 로그인)에 적절한 사용 권한이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-110">It is assumed that the database is set up correctly and that the user context (that is, the login that Bulk Load is set use) has appropriate permissions set.</span></span>  
  
-   <span data-ttu-id="8b932-111">비트랜잭션 모드에서 대량 로드 프로세스 중에 오류가 발생하면 데이터가 부분 로드된 상태로 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-111">In non-transactional mode, if an error occurs during the Bulk Load process, data may be left in a partially loaded state.</span></span> <span data-ttu-id="8b932-112">이 오류가 발생하는 시점에 해당 위치에서 대량 로드가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-112">Bulk Load will simply stop at the point where it is when this happens.</span></span> <span data-ttu-id="8b932-113">트랜잭션 모드를 사용하면 이 문제를 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-113">Transactional mode can be used to alleviate this issue.</span></span>  
  
-   <span data-ttu-id="8b932-114">대량 로드 오류가 발생할 때 오류 정보에 데이터베이스에 대한 정보가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-114">When Bulk Load errors occur, they may include information about the database.</span></span> <span data-ttu-id="8b932-115">예를 들어 테이블이나 열 이름 또는 열 형식 정보가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-115">For example, they may include the name of a table or column, or column type information.</span></span> <span data-ttu-id="8b932-116">대량 로드를 사용할 때는 오류를 사용자에게 직접 노출하기 보다는 대량 로드 프로세스에서 오류를 catch하고 일반 오류 메시지를 반환하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-116">When you use Bulk Load, you should take care to catch errors from the Bulk Load process and return a generic error message, rather than exposing errors directly to users.</span></span>  
  
-   <span data-ttu-id="8b932-117">대량 로드 작업에서 처리할 수 있는 데이터 양에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-117">Bulk Load sets no limit on the amount of data it works over.</span></span> <span data-ttu-id="8b932-118">대량 로드에서는 로드할 데이터의 크기를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-118">Bulk Load does not do any checking on the size of the data to be loaded.</span></span> <span data-ttu-id="8b932-119">대량 로드 작업을 실행할 때 지정한 파일을 처리하는 데 필요한 메모리가 충분한지, 그리고 로드하는 데이터를 저장할 공간이 데이터베이스에 있는지는 사용자가 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-119">It is the responsibility of the user executing Bulk Load to ensure that there is enough memory to process the specified file, and that there is enough room in the database to store the data being loaded.</span></span>  
  
-   <span data-ttu-id="8b932-120">대량 로드에서는 코드로 지정된 데이터를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-120">Bulk Load does not make an attempt to use the data it is given as code.</span></span> <span data-ttu-id="8b932-121">또한 데이터 입력을 어떠한 방식으로든 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-121">The data input is never executed in any fashion.</span></span> <span data-ttu-id="8b932-122">입력 데이터의 모든 코드나 명령은 일반 데이터로 처리되며 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-122">Any code or commands in the input data are treated as normal data and will not be executed.</span></span>  
  
-   <span data-ttu-id="8b932-123">대량 로드에서는 XML과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 모델 간의 차이를 기준으로 지정된 데이터의 형식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-123">Bulk Load may make formatting changes to the given data based on differences between the XML and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data models.</span></span> <span data-ttu-id="8b932-124">예를 들어 시간을 지정하는 형식이 다를 경우</span><span class="sxs-lookup"><span data-stu-id="8b932-124">For example, the format for specifying a time is different.</span></span> <span data-ttu-id="8b932-125">대량 로드에서 이러한 차이를 해결하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-125">Bulk Load will attempt to resolve these differences.</span></span> <span data-ttu-id="8b932-126">따라서 일부 전체 자릿수 정보가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-126">As a result, some precision information may be lost.</span></span>  
  
-   <span data-ttu-id="8b932-127">대량 로드에서는 데이터를 처리하는 데 걸리는 시간에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-127">Bulk Load sets no limit on the amount of time it takes to process the data.</span></span> <span data-ttu-id="8b932-128">처리가 완료되거나 오류가 발생할 때까지 처리 작업이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-128">Processing will continue until processing is complete or an error occurs.</span></span>  
  
-   <span data-ttu-id="8b932-129">대량 로드에서는 데이터베이스 내에서 임시 테이블을 만들거나 삭제할 수 있으므로 이 작업을 위한 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-129">Bulk Load can create and delete temporary tables within the database, and needs permissions to do so.</span></span> <span data-ttu-id="8b932-130">이러한 테이블에 대한 사용 권한은 대량 로드 프로세스를 위해 데이터베이스에 연결하고 있는 동일한 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-130">Permissions to these tables will be given to the same user who is connecting to the database for the Bulk Load process.</span></span>  
  
-   <span data-ttu-id="8b932-131">대량 로드에서는 트랜잭션 모드 처리 동안 사용되는 임시 파일을 만들거나 삭제할 수 있으므로 이 작업을 위한 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-131">Bulk Load can create and delete temporary files used during transactional mode processing, and needs permissions to do so.</span></span> <span data-ttu-id="8b932-132">이러한 파일은 대량 로드가 실행되고 있는 스레드의 현재 사용자와 동일한 사용 권한으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-132">These files are created with the same permissions as the current user of the thread within which Bulk Load is running.</span></span>  
  
-   <span data-ttu-id="8b932-133">사용자가 SQLXML에서 오류를 기록할 오류 로그 파일을 설정하는 경우 대량 로드를 실행할 때마다 이 파일이 마지막 대량 로드 프로세스의 데이터로 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="8b932-133">If the user sets an error Log file for SQLXML to write errors into, then each time Bulk Load is executed the file will be overwritten with data from the last Bulk Load process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b932-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b932-134">See Also</span></span>  
 [<span data-ttu-id="8b932-135">XML 데이터 대량 로드 수행&#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="8b932-135">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
