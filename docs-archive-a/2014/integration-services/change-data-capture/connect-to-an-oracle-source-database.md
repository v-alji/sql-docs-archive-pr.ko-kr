---
title: Oracle 원본 데이터베이스에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fccba3d11adc67b3f5ef4f8648ec5d0de07a5648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735520"
---
# <a name="connect-to-an-oracle-source-database"></a><span data-ttu-id="5c9d8-102">Oracle 원본 데이터베이스에 연결</span><span class="sxs-lookup"><span data-stu-id="5c9d8-102">Connect to an Oracle Source Database</span></span>
  <span data-ttu-id="5c9d8-103">Oracle 원본 페이지를 사용하여 Oracle 원본 데이터베이스에 연결하는 데 필요한 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-103">Use the Oracle Source page to provide the information necessary to connect to the Oracle source database.</span></span> <span data-ttu-id="5c9d8-104">CDC 인스턴스는 연결된 Oracle 데이터베이스의 다시 실행 로그를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-104">The CDC instance will read the redo logs of the Oracle database you are connected to.</span></span>  
  
 <span data-ttu-id="5c9d8-105">**Oracle 연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="5c9d8-105">**Oracle Connect String**</span></span>  
 <span data-ttu-id="5c9d8-106">사용 중인 Oracle 데이터베이스가 있는 컴퓨터에 대한 Oracle 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-106">Enter the Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="5c9d8-107">연결 문자열은 다음 중 한 가지 방법으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-107">The connect string is written in one of the following ways:</span></span>  
  
 `host[:port][/service name]`  
  
 <span data-ttu-id="5c9d8-108">연결 문자열에서 Oracle Net 연결 설명자를 지정할 수도 있습니다(예: `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span><span class="sxs-lookup"><span data-stu-id="5c9d8-108">The connection string can also specify an Oracle Net connect descriptor, for example, `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span></span>  
  
 <span data-ttu-id="5c9d8-109">디렉터리 서버 또는 tnsnames를 사용하는 경우 연결 문자열이 연결의 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-109">If using a directory server or tnsnames, the connect string can be the name of the connection.</span></span>  
  
 <span data-ttu-id="5c9d8-110">**Oracle 로그 마이닝 인증**</span><span class="sxs-lookup"><span data-stu-id="5c9d8-110">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="5c9d8-111">로그 마이닝에 대한 권한이 있는 Oracle 데이터베이스 사용자의 자격 증명을 입력하려면 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-111">To enter the credentials for the Oracle database user that is authorized for log mining, select one of the following:</span></span>  
  
-   <span data-ttu-id="5c9d8-112">**Windows 인증**: 현재 Windows 도메인 자격 증명을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-112">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="5c9d8-113">Windows 인증을 사용하도록 Oracle 데이터베이스를 구성한 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-113">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="5c9d8-114">**Oracle 인증**: 이 옵션을 선택하는 경우 연결 중인 Oracle 데이터베이스의 사용자에 대한 **사용자 이름** 과 **암호** 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-114">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c9d8-115">사용자가 로그 마이닝 사용자가 되려면 Oracle 데이터베이스에 다음 권한이 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-115">A user must have the following privileges granted in the Oracle database to be a log-mining user.</span></span>  
> 
>  -   <span data-ttu-id="5c9d8-116">\<any-captured-table>에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-116">SELECT on \<any-captured-table></span></span>  
> -   <span data-ttu-id="5c9d8-117">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="5c9d8-117">SELECT ANY TRANSACTION</span></span>  
> -   <span data-ttu-id="5c9d8-118">DBMS LOGMNR에 대한 EXECUTE 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-118">EXECUTE on DBMS LOGMNR</span></span>  
> -   <span data-ttu-id="5c9d8-119">V$LOGMNR CONTENTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-119">SELECT on V$LOGMNR CONTENTS</span></span>  
> -   <span data-ttu-id="5c9d8-120">V$ARCHIVED LOG에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-120">SELECT on V$ARCHIVED LOG</span></span>  
> -   <span data-ttu-id="5c9d8-121">V$LOG에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-121">SELECT on V$LOG</span></span>  
> -   <span data-ttu-id="5c9d8-122">V$LOGFILE에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-122">SELECT on V$LOGFILE</span></span>  
> -   <span data-ttu-id="5c9d8-123">V$DATABASE에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-123">SELECT on V$DATABASE</span></span>  
> -   <span data-ttu-id="5c9d8-124">V$THREAD에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-124">SELECT on V$THREAD</span></span>  
> -   <span data-ttu-id="5c9d8-125">ALL INDEXES에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-125">SELECT on ALL INDEXES</span></span>  
> -   <span data-ttu-id="5c9d8-126">ALL OBJECTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-126">SELECT on ALL OBJECTS</span></span>  
> -   <span data-ttu-id="5c9d8-127">DBA OBJECTS에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-127">SELECT on DBA OBJECTS</span></span>  
> -   <span data-ttu-id="5c9d8-128">ALL TABLES에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="5c9d8-128">SELECT on ALL TABLES</span></span>  
> 
>  <span data-ttu-id="5c9d8-129">이러한 권한을 V$xxx에 부여할 수 없는 경우 V_S$xxx에 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-129">If any of these privileges cannot be granted to a V$xxx, then grant them to the V_S$xxx.</span></span>  
  
 <span data-ttu-id="5c9d8-130">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="5c9d8-130">**Test Connection**</span></span>  
 <span data-ttu-id="5c9d8-131">**연결 테스트** 를 클릭하여 Oracle 데이터베이스가 있는 원격 컴퓨터와의 연결되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-131">Click **Test Connection** to determine whether you established a connection with the remote computer that has the Oracle database.</span></span> <span data-ttu-id="5c9d8-132">연결에 성공했는지 여부를 알려주는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-132">A dialog box opens to inform you whether the connection was successful.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5c9d8-133">CDC Designer를 관리자 권한으로 실행하지 않을 경우 알려진 문제로 인해 Oracle 원본 데이터베이스에 연결하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-133">Due to a known issue connection to the Oracle source database may fail if the CDC Designer is not run as an administrator.</span></span> <span data-ttu-id="5c9d8-134">연결이 실패하는 경우 CDC Designer를 닫은 후 **관리자 권한으로 실행** 옵션을 사용하여 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-134">If connection fails, close and restart the CDC Designer using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="5c9d8-135">이 페이지에서 정보 입력을 마친 후 **다음** 을 클릭하여 [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md)을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5c9d8-135">After you finish entering information on this page, click **Next** to [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9d8-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c9d8-136">See Also</span></span>  
 <span data-ttu-id="5c9d8-137">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="5c9d8-137">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="5c9d8-138">인스턴스 속성 편집</span><span class="sxs-lookup"><span data-stu-id="5c9d8-138">Edit Instance Properties</span></span>](edit-instance-properties.md)  
  
  
