---
title: Oracle 게시자 문제 해결 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], troubleshooting
- troubleshooting [SQL Server replication], Oracle publishing
ms.assetid: be94f1c1-816b-4b1d-83f6-2fd6f5807ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4097b2c185b6dde307cd9b295d3b5b32f5797649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648922"
---
# <a name="troubleshooting-oracle-publishers"></a><span data-ttu-id="a24c5-102">Oracle 게시자 문제 해결</span><span class="sxs-lookup"><span data-stu-id="a24c5-102">Troubleshooting Oracle Publishers</span></span>
  <span data-ttu-id="a24c5-103">이 항목에서는 Oracle 게시자를 구성 및 사용할 때 발생할 수 있는 여러 가지 문제를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-103">This topic lists a number of issues that might arise when configuring and using an Oracle Publisher.</span></span>  
  
## <a name="an-error-is-raised-regarding-oracle-client-and-networking-software"></a><span data-ttu-id="a24c5-104">Oracle 클라이언트 및 네트워킹 소프트웨어와 관련된 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-104">An Error Is Raised Regarding Oracle Client and Networking Software</span></span>  
 <span data-ttu-id="a24c5-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 배포자에서 실행되는 계정에는 Oracle 클라이언트 네트워킹 소프트웨어가 설치된 디렉터리 및 모든 하위 디렉터리에 대한 읽기 및 실행 권한이 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-105">The account under which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs on the Distributor must be granted read and execute permissions for the directory (and all subdirectories) in which the Oracle client networking software is installed.</span></span> <span data-ttu-id="a24c5-106">사용 권한이 부여되지 않거나 Oracle 클라이언트 구성 요소가 제대로 설치되지 않으면 다음과 같은 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-106">If the permissions are not granted or the Oracle client components are not installed properly, you will receive the following error message:</span></span>  
  
 <span data-ttu-id="a24c5-107">"[Microsoft OLE DB Provider for Oracle]로 서버에 연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-107">"Connection to server failed with [Microsoft OLE DB Provider for Oracle].</span></span> <span data-ttu-id="a24c5-108">Oracle 클라이언트 및 네트워킹 구성 요소를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-108">Oracle client and networking components were not found.</span></span> <span data-ttu-id="a24c5-109">이러한 구성 요소는 Oracle 버전 7.3.3 이상의 클라이언트 소프트웨어 설치의 일부로 Oracle사에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-109">These components are supplied by Oracle Corporation and are part of the Oracle Version 7.3.3 or later client software installation.</span></span> <span data-ttu-id="a24c5-110">이러한 구성 요소를 설치해야 공급자를 사용할 수 있습니다."</span><span class="sxs-lookup"><span data-stu-id="a24c5-110">Provider is unable to function until these components are installed."</span></span>  
  
 <span data-ttu-id="a24c5-111">해당 Oracle 클라이언트가 배포자에 설치된 경우 클라이언트 설치가 완료된 후에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 중지되었다가 다시 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-111">If an appropriate Oracle client has been installed at the Distributor, ensure that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] was stopped and then restarted after the client installation completed.</span></span> <span data-ttu-id="a24c5-112">이렇게 해야 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 클라이언트 구성 요소를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-112">This is required in order for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to recognize the client components.</span></span>  
  
 <span data-ttu-id="a24c5-113">권한을 부여하고 구성 요소를 올바르게 설치한 다음에도 이 오류가 계속 발생하면 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI의 레지스트리 설정이 올바른지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-113">If you have verified that permissions are granted and that components are installed correctly, but this error persists, verify that the registry settings at HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI are correct:</span></span>  
  
-   <span data-ttu-id="a24c5-114">Oracle 10g의 경우 올바른 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-114">For Oracle 10g, the correct settings are</span></span>  
  
    -   <span data-ttu-id="a24c5-115">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-115">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="a24c5-116">OracleSqlLib = orasql10.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-116">OracleSqlLib = orasql10.dll</span></span>  
  
    -   <span data-ttu-id="a24c5-117">OracleXaLib = oraclient10.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-117">OracleXaLib = oraclient10.dll</span></span>  
  
-   <span data-ttu-id="a24c5-118">Oracle 9i의 경우 올바른 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-118">For Oracle 9i, the correct settings are</span></span>  
  
    -   <span data-ttu-id="a24c5-119">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-119">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="a24c5-120">OracleSqlLib = orasql9.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-120">OracleSqlLib = orasql9.dll</span></span>  
  
    -   <span data-ttu-id="a24c5-121">OracleXaLib = oraclient9.dll</span><span class="sxs-lookup"><span data-stu-id="a24c5-121">OracleXaLib = oraclient9.dll</span></span>  
  
## <a name="the-sql-server-distributor-cannot-connect-to-the-oracle-database-instance"></a><span data-ttu-id="a24c5-122">SQL Server 배포자가 Oracle 데이터베이스 인스턴스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-122">The SQL Server Distributor Cannot Connect to the Oracle Database Instance</span></span>  
 <span data-ttu-id="a24c5-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자가 Oracle 게시자에 연결할 수 없는 경우 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-123">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, ensure that:</span></span>  
  
-   <span data-ttu-id="a24c5-124">필요한 Oracle 소프트웨어가 배포자에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-124">The necessary Oracle software is installed on the Distributor.</span></span>  
  
-   <span data-ttu-id="a24c5-125">Oracle 데이터베이스가 온라인 상태이고 SQL\*Plus와 같은 도구를 사용하여 이 데이터베이스에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-125">The Oracle database is online and you can connect to it using a tool like SQL\*Plus.</span></span>  
  
-   <span data-ttu-id="a24c5-126">복제에서 Oracle 게시자 연결에 사용하는 로그인에 충분한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-126">The login replication uses to connect to the Oracle Publisher has sufficient permissions.</span></span> <span data-ttu-id="a24c5-127">자세한 내용은 [Oracle 게시자 구성](configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-127">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
-   <span data-ttu-id="a24c5-128">Oracle 게시자를 구성하는 동안 정의된 TNS 이름이 tnsnames.ora 파일에 나열되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-128">The TNS names defined during configuration of the Oracle Publisher are listed in the tnsnames.ora file.</span></span>  
  
-   <span data-ttu-id="a24c5-129">올바른 Oracle 홈 및 경로를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-129">The correct Oracle Home and path are used.</span></span> <span data-ttu-id="a24c5-130">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에 하나의 Oracle 바이너리 집합만 설치한 경우에도 Oracle 홈과 관련된 환경 변수를 제대로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-130">Even if you have only one set of Oracle binaries installed on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, ensure that the environment variables related to the Oracle Home are set properly.</span></span> <span data-ttu-id="a24c5-131">환경 변수 값을 변경한 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 중지하고 다시 시작하여 변경 내용을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-131">If you change environment variable values, you must stop and restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for the change to take effect.</span></span>  
  
 <span data-ttu-id="a24c5-132">연결을 구성 및 테스트하는 방법은 [Oracle 게시자 구성](configure-an-oracle-publisher.md)의 "[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에 Oracle 클라이언트 네트워킹 소프트웨어 설치 및 구성"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-132">For more information about configuring and testing connectivity, see "Installing and Configuring Oracle Client Networking Software on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="the-oracle-publisher-is-associated-with-another-distributor"></a><span data-ttu-id="a24c5-133">Oracle 게시자가 다른 배포자와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-133">The Oracle Publisher Is Associated with Another Distributor</span></span>  
 <span data-ttu-id="a24c5-134">Oracle 게시자는 한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-134">An Oracle Publisher can only be associated with one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="a24c5-135">Oracle 게시자에 배포자가 연결되어 있는 경우 다른 배포자를 사용하려면 먼저 기존 배포자를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-135">If a different Distributor is associated with the Oracle Publisher, it must be dropped before another Distributor can be used.</span></span> <span data-ttu-id="a24c5-136">기존 배포자를 먼저 삭제하지 않으면 다음 오류 메시지 중 하나가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-136">If the Distributor is not dropped first, you will receive one of the following error messages:</span></span>  
  
-   <span data-ttu-id="a24c5-137">"'\<*SQLServerDistributorName*>'을(를) 배포자로 사용하도록 Oracle 서버 인스턴스 '\<*OraclePublisherName*>'이(가) 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-137">"Oracle server instance '\<*OraclePublisherName*>' has been previously configured to use '\<*SQLServerDistributorName*>' as its Distributor.</span></span> <span data-ttu-id="a24c5-138">'\<*NewSQLServerDistributorName*>'을(를) 배포자로 사용하려면 Oracle 서버 인스턴스의 현재 복제 구성을 제거하여 해당 서버 인스턴스의 모든 게시를 삭제해야 합니다."</span><span class="sxs-lookup"><span data-stu-id="a24c5-138">To begin using '\<*NewSQLServerDistributorName*>' as its Distributor, you must remove the current replication configuration on the Oracle server instance, which will delete all publications on that server instance."</span></span>  
  
-   <span data-ttu-id="a24c5-139">"Oracle 서버 '\<*OracleServerName*>'은(는) 배포자 '\<*SQLServerDistributorName*>. *\<DistributionDatabaseName>* '에서 이미 게시자 '\<*OraclePublisherName*>'(으)로 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-139">"Oracle server '\<*OracleServerName*>' is already defined as publisher '\<*OraclePublisherName*>' on distributor '\<*SQLServerDistributorName*>.*\<DistributionDatabaseName>*'.</span></span> <span data-ttu-id="a24c5-140">게시자를 삭제하거나 공용 동의어 ' *\<SynonymName>* '을(를) 삭제하고 다시 만드십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-140">Drop the publisher or drop the public synonym '*\<SynonymName>*' to recreate."</span></span>  
  
 <span data-ttu-id="a24c5-141">Oracle 게시자를 삭제하면 Oracle 데이터베이스의 복제 개체가 자동으로 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-141">When an Oracle Publisher is dropped, the replication objects in the Oracle database are automatically cleaned up.</span></span> <span data-ttu-id="a24c5-142">그러나 어떤 경우에는 Oracle 복제 개체를 수동으로 정리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-142">However, manual cleanup of the Oracle replication objects is necessary in some cases.</span></span> <span data-ttu-id="a24c5-143">복제에 의해 생성된 Oracle 복제 개체를 수동으로 정리하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-143">To manually clean up Oracle replication objects created by replication:</span></span>  
  
1.  <span data-ttu-id="a24c5-144">DBA 권한으로 Oracle 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-144">Connect to the Oracle publisher with DBA permissions.</span></span>  
  
2.  <span data-ttu-id="a24c5-145">SQL 명령 `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-145">Issue the SQL command `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`.</span></span>  
  
3.  <span data-ttu-id="a24c5-146">SQL 명령 `DROP USER <replication_administrative_user_schema>``CASCADE;`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-146">Issue the SQL command `DROP USER <replication_administrative_user_schema>``CASCADE;`.</span></span>  
  
## <a name="sql-server-error-21663-is-raised-regarding-the-lack-of-a-primary-key"></a><span data-ttu-id="a24c5-147">PRIMARY KEY 부재와 관련된 SQL Server 오류 21663이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-147">SQL Server Error 21663 Is Raised Regarding the Lack of a Primary Key</span></span>  
 <span data-ttu-id="a24c5-148">트랜잭션 게시의 아티클에는 올바른 기본 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-148">Articles in transactional publications must have a valid primary key.</span></span> <span data-ttu-id="a24c5-149">아티클에 올바른 기본 키가 없으면 아티클을 추가할 때 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-149">If they do not have a valid primary key, you will receive the following error message when you attempt to add an article:</span></span>  
  
 <span data-ttu-id="a24c5-150">"원본 테이블 [\<*TableOwner*>].[\<*TableName*>]에 대해 올바른 기본 키를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="a24c5-150">"No valid primary key found for source table [\<*TableOwner*>].[\<*TableName*>]"</span></span>  
  
 <span data-ttu-id="a24c5-151">기본 키 요구 사항에 대한 자세한 내용은 [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md)항목의 "고유 인덱스 및 UNIQUE 제약 조건" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-151">For information about requirements for primary keys, see the section "Unique Indexes and Constraints" in the topic [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md).</span></span>  
  
## <a name="sql-server-error-21642-is-raised-regarding-a-duplicate-linked-server-login"></a><span data-ttu-id="a24c5-152">연결된 서버로의 중복 로그인과 관련된 SQL Server 오류 21642가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-152">SQL Server Error 21642 Is Raised Regarding a Duplicate Linked Server Login</span></span>  
 <span data-ttu-id="a24c5-153">Oracle 게시자를 처음 구성하면 게시자와 배포자 간 연결에 대해 연결된 서버 항목이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-153">When an Oracle Publisher is initially configured, a linked server entry is created for the connection between the Publisher and the Distributor.</span></span> <span data-ttu-id="a24c5-154">연결된 서버의 이름은 Oracle TNS 서비스 이름과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-154">The linked server has the same name as the Oracle TNS service name.</span></span> <span data-ttu-id="a24c5-155">이름이 동일한 연결된 서버를 만들면 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-155">If you attempt to create a linked server with the same name, the following error message is shown:</span></span>  
  
 <span data-ttu-id="a24c5-156">"유형이 다른 게시자에는 연결된 서버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-156">"Heterogeneous publishers require a linked server.</span></span> <span data-ttu-id="a24c5-157">이름이 ' *\<LinkedServerName>* '인 연결된 서버가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-157">A linked server named '*\<LinkedServerName>*' already exists.</span></span> <span data-ttu-id="a24c5-158">연결된 서버를 제거하거나 다른 게시자 이름을 선택하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-158">Please remove linked server or choose a different publisher name."</span></span>  
  
 <span data-ttu-id="a24c5-159">이 오류는 연결된 서버를 직접 만들거나 이전에 삭제한 Oracle 게시자와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자 간 관계를 다시 구성하려고 하는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-159">This error can occur if you attempt to create the linked server directly or if you have previously dropped the relationship between the Oracle Publisher and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, and you are now attempting to reconfigure it.</span></span> <span data-ttu-id="a24c5-160">게시자를 다시 구성하는 동안 이 오류가 표시되면 [sp_dropserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql)를 사용하여 연결된 서버를 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-160">If you receive this error while attempting to reconfigure the Publisher, drop the linked server with [sp_dropserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql).</span></span>  
  
 <span data-ttu-id="a24c5-161">연결된 서버 연결을 통해 Oracle 게시자에 연결하려면 다른 TNS 서비스 이름을 만든 다음 이 이름을 사용하여 [sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-161">If you need to connect to the Oracle Publisher over a linked server connection, create another TNS service name, and then use this name when calling [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="a24c5-162">TNS 서비스 이름을 만드는 방법은 Oracle 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-162">For information about creating TNS service names, see the Oracle documentation.</span></span>  
  
## <a name="sql-server-error-21617-is-raised"></a><span data-ttu-id="a24c5-163">SQL Server 오류 21617이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-163">SQL Server Error 21617 Is Raised</span></span>  
 <span data-ttu-id="a24c5-164">Oracle 게시는 Oracle 애플리케이션 SQL\*PLUS를 사용하여 게시자 지원 코드 패키지를 Oracle 데이터베이스로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-164">Oracle publishing uses the Oracle application SQL\*PLUS to download the package of Publisher support code to the Oracle database.</span></span> <span data-ttu-id="a24c5-165">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 Oracle 게시자를 구성하기 전에 배포자에서 시스템 경로로 SQL\*PLUS에 액세스할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-165">Before attempting to configure the Oracle Publisher, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verifies that SQL\*PLUS is accessible through the system path on the Distributor.</span></span> <span data-ttu-id="a24c5-166">SQL\*PLUS를 로드할 수 없으면 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-166">If SQL\*PLUS cannot be loaded, the following error message is shown:</span></span>  
  
 <span data-ttu-id="a24c5-167">"SQL\*PLUS를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-167">"Unable to run SQL\*PLUS.</span></span> <span data-ttu-id="a24c5-168">배포자에 최신 버전의 Oracle 클라이언트 코드가 설치되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-168">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="a24c5-169">배포자에서 SQL\*PLUS를 찾으세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-169">Try to locate SQL\*PLUS on the Distributor.</span></span> <span data-ttu-id="a24c5-170">Oracle 10g 클라이언트 설치의 경우 이 실행 파일의 이름은 sqlplus.exe입니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-170">For an Oracle 10g client install, the name of this executable is sqlplus.exe.</span></span> <span data-ttu-id="a24c5-171">이 파일은 일반적으로 %ORACLE_HOME%/bin에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-171">It is typically installed in %ORACLE_HOME%/bin.</span></span> <span data-ttu-id="a24c5-172">SQL\*PLUS의 경로가 시스템 경로에 표시되는지 확인하려면 시스템 변수 **Path** 값을 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-172">To verify that the path of SQL\*PLUS appears in the system path, examine the value of the system variable **Path**:</span></span>  
  
1.  <span data-ttu-id="a24c5-173">**내 컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-173">Right-click **My Computer**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a24c5-174">**고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-174">Click the **Advanced** tab, and then click **Environment variables**.</span></span>  
  
3.  <span data-ttu-id="a24c5-175">**환경 변수** 대화 상자의 **시스템 변수** 목록에서 **Path** 변수를 선택한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-175">In the **Environment Variables** dialog box, in the **System variables** list, select the **Path** variable, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="a24c5-176">**시스템 변수 편집** 대화 상자에서 sqlplus.exe가 들어 있는 폴더의 경로가 **변수 값** 입력란에 나타나지 않으면 해당 문자열을 편집하여 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-176">In the **Edit System Variable** dialog box: if the path to the folder that contains sqlplus.exe is not present in the **Variable value** text box, edit the string to include it.</span></span>  
  
5.  <span data-ttu-id="a24c5-177">열려 있는 각 대화 상자에서 **확인** 을 클릭하여 변경 내용을 저장하고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-177">Click **OK** on each open dialog box to exit and save changes.</span></span>  
  
 <span data-ttu-id="a24c5-178">배포자에서 sqlplus.exe를 찾을 수 없으면 배포자에 최신 버전의 Oracle 클라이언트 소프트웨어를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-178">If you cannot locate sqlplus.exe on the Distributor, install a current version of the Oracle client software at the Distributor.</span></span> <span data-ttu-id="a24c5-179">자세한 내용은 [Oracle 게시자 구성](configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-179">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="sql-server-error-21620-is-raised"></a><span data-ttu-id="a24c5-180">SQL Server 오류 21620이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-180">SQL Server Error 21620 Is Raised</span></span>  
 <span data-ttu-id="a24c5-181">Oracle 데이터베이스 8.1 이전 버전에 연결하는 경우 Oracle 게시를 위해 배포자에 설치된 Oracle 클라이언트 소프트웨어는 버전 9여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-181">If you are connecting to an Oracle database earlier than version 8.1, Oracle publishing requires that the Oracle client software installed on the Distributor be from version 9.</span></span> <span data-ttu-id="a24c5-182">Oracle 데이터베이스 8.1 이후 버전에 연결하는 경우에는 버전 10 이상의 Oracle 클라이언트 소프트웨어를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-182">If you are connecting to an Oracle database that is version 8.1 or later, we recommend that the Oracle client software be version 10 or later.</span></span>  
  
 <span data-ttu-id="a24c5-183">Oracle 게시는 Oracle 게시자를 구성하기 전에 배포자에서 시스템 경로로 액세스할 수 있는 SQL\*PLUS가 버전 9 이상인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-183">Before attempting to configure the Oracle Publisher, Oracle publishing verifies that the version of SQL\*PLUS accessible through the system path on the Distributor is version 9 or later.</span></span> <span data-ttu-id="a24c5-184">버전 9 이상이 아니면 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-184">If it is not, the following error message is shown:</span></span>  
  
 <span data-ttu-id="a24c5-185">"시스템 경로 변수로 액세스할 수 있는 SQL\*PLUS 버전이 최신 버전이 아니어서 Oracle 게시를 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-185">"The version of SQL\*PLUS that is accessible through the system Path variable is not current enough to support Oracle publishing.</span></span> <span data-ttu-id="a24c5-186">배포자에 최신 버전의 Oracle 클라이언트 코드가 설치되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-186">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="a24c5-187">여러 버전의 Oracle 클라이언트 소프트웨어가 배포자에 설치되어 있을 경우 최신 버전이 버전 9 이상이며 시스템 경로 변수가 먼저 이 버전을 가리키는지 확인하십시오. 최신 버전이 먼저 표시되기만 하면 다른 버전에 대한 참조도 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-187">If you have multiple versions of the Oracle client software installed on the Distributor, make sure that the most current version is at least version 9 and that the system path variable refers first to this version (references to other versions can appear as long as the most recent appears first).</span></span> <span data-ttu-id="a24c5-188">시스템 경로 변수를 편집하는 방법은 이 항목의 앞부분에 있는 "SQL Server 오류 21617이 발생합니다" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-188">For more information about editing the system path variable, see the section "SQL Server Error 21617 is Raised" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21624-or-error-21629-is-raised"></a><span data-ttu-id="a24c5-189">SQL Server 오류 21624 또는 오류 21629가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-189">SQL Server Error 21624 or Error 21629 Is Raised</span></span>  
 <span data-ttu-id="a24c5-190">64비트 배포자의 경우 Oracle 게시는 Oracle OLEDB 공급자(OraOLEDB.Oracle)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-190">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> <span data-ttu-id="a24c5-191">배포자에 Oracle OLEDB 공급자가 설치 및 등록되었는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-191">Make sure that the Oracle OLEDB provider is installed and registered on the Distributor.</span></span> <span data-ttu-id="a24c5-192">공급자가 설치 및 등록되어 있지 않으면 다음 오류 메시지 중 하나 또는 둘 다가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-192">If the provider is not installed and registered, one or both of the following error messages is shown:</span></span>  
  
-   <span data-ttu-id="a24c5-193">"배포자 '%s'에서 Oracle OLEDB 공급자 OraOLEDB.Oracle을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-193">"Unable to locate the registered Oracle OLEDB provider, OraOLEDB.Oracle, at distributor '%s'.</span></span> <span data-ttu-id="a24c5-194">배포자에 최신 버전의 Oracle OLEDB 공급자가 설치 및 등록되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-194">Make certain that a current version of the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
-   <span data-ttu-id="a24c5-195">"Oracle OLEDB 공급자 OraOLEDB.Oracle이 등록되었음을 나타내는 CLSID 레지스트리 키가 배포자에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-195">"The CLSID registry key indicating that the Oracle OLEDB Provider for Oracle, OraOLEDB.Oracle, has been registered is not present at the distributor.</span></span> <span data-ttu-id="a24c5-196">배포자에 Oracle OLEDB 공급자가 설치 및 등록되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-196">Make certain that the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
 <span data-ttu-id="a24c5-197">Oracle 클라이언트 소프트웨어 버전 10g를 사용하는 경우 공급자는 OraOLEDB10.dll입니다. 버전 9i의 경우에는 OraOLEDB.dll입니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-197">If you are using Oracle client software version 10g, the provider is OraOLEDB10.dll; for version 9i, it is OraOLEDB.dll.</span></span> <span data-ttu-id="a24c5-198">공급자는 %ORACLE_HOME%\BIN에 설치됩니다(예: C:\oracle\product\10.1.0\Client_1\bin).</span><span class="sxs-lookup"><span data-stu-id="a24c5-198">The provider is installed in %ORACLE_HOME%\BIN (for example, C:\oracle\product\10.1.0\Client_1\bin).</span></span> <span data-ttu-id="a24c5-199">배포자에 Oracle OLEDB 공급자가 설치되어 있지 않으면 Oracle에서 제공한 Oracle 클라이언트 소프트웨어 설치 디스크에서 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-199">If you determine that the Oracle OLEDB provider is not installed on the Distributor, install it from the Oracle client software install disc provided by Oracle.</span></span> <span data-ttu-id="a24c5-200">자세한 내용은 [Oracle 게시자 구성](configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-200">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="a24c5-201">Oracle OLEDB 공급자가 설치되어 있으면 등록되었는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-201">If the Oracle OLEDB provider is installed, make sure that it is registered.</span></span> <span data-ttu-id="a24c5-202">공급자 DLL을 등록하려면 DLL이 설치된 디렉터리에서 다음 명령을 실행한 다음 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 중지했다가 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-202">To register the provider DLL, execute the following command from the directory in which the DLL is installed, and then stop and restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="a24c5-203">`regsvr32 OraOLEDB10.dll` 또는 `regsvr32 OraOLEDB.dll`입니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-203">`regsvr32 OraOLEDB10.dll` or `regsvr32 OraOLEDB.dll`.</span></span>  
  
## <a name="sql-server-error-21626-or-error-21627-is-raised"></a><span data-ttu-id="a24c5-204">SQL Server 오류 21626 또는 오류 21627이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-204">SQL Server Error 21626 or Error 21627 Is Raised</span></span>  
 <span data-ttu-id="a24c5-205">Oracle 게시 환경이 올바로 구성되었는지 확인하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 구성 중에 지정한 로그인 자격 증명을 사용하여 Oracle 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-205">To verify that the Oracle publishing environment is configured properly, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tries to connect to the Oracle Publisher with the login credentials you specified during configuration.</span></span> <span data-ttu-id="a24c5-206">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자가 Oracle 게시자에 연결할 수 없는 경우 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-206">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, the following error message is shown:</span></span>  
  
-   <span data-ttu-id="a24c5-207">"Oracle OLEDB 공급자 OraOLEDB.Oracle을 사용하여 Oracle 데이터베이스 서버 '%s'에 연결할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="a24c5-207">"Unable to connect to Oracle database server '%s' using the Oracle OLEDB provider OraOLEDB.Oracle."</span></span>  
  
 <span data-ttu-id="a24c5-208">이 오류 메시지가 표시되면 Oracle 게시자 구성 중에 지정한 로그인 및 암호로 직접 SQL\*PLUS를 실행하여 Oracle 데이터베이스에 대한 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-208">If this error message is shown, verify connectivity to the Oracle database by running SQL\*PLUS directly using the same login and password specified during configuration of the Oracle Publisher.</span></span> <span data-ttu-id="a24c5-209">자세한 내용은 이 항목의 앞부분에 있는 "SQL Server 배포자가 Oracle 데이터베이스 인스턴스에 연결할 수 없습니다" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-209">For more information, see the section "The SQL Server Distributor Cannot Connect to the Oracle Database Instance" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21628-is-raised"></a><span data-ttu-id="a24c5-210">SQL Server 오류 21628이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-210">SQL Server Error 21628 Is Raised</span></span>  
 <span data-ttu-id="a24c5-211">64비트 배포자의 경우 Oracle 게시는 Oracle OLEDB 공급자(OraOLEDB.Oracle)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-211">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a24c5-212">는 Oracle 공급자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]프로세스에서 실행되도록 허용하기 위해 레지스트리 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-212">creates a registry entry to allow the Oracle provider to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a24c5-213">이 레지스트리 항목을 읽거나 쓰는 데 문제가 있으면 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-213">If there is a problem reading or writing this registry entry, the following error message is shown:</span></span>  
  
 <span data-ttu-id="a24c5-214">"Oracle OLEDB 공급자 OraOLEDB.Oracle이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]프로세스에서 실행되도록 허용하기 위해 배포자 '%s'의 레지스트리를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-214">"Unable to update the registry of distributor '%s' to allow Oracle OLEDB provider OraOLEDB.Oracle to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a24c5-215">현재 로그인에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 소유 레지스트리 키를 수정할 권한이 부여되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="a24c5-215">Make certain that current login is authorized to modify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] owned registry keys."</span></span>  
  
 <span data-ttu-id="a24c5-216">Oracle 게시는 레지스트리 항목이 있어야 하며 64비트 배포자의 경우 **1** 로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-216">Oracle publishing requires the registry entry to exist and to be set to **1** for 64 bit Distributors.</span></span> <span data-ttu-id="a24c5-217">항목이 없으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-217">If the entry does not exist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will attempt to create it.</span></span> <span data-ttu-id="a24c5-218">항목이 있지만 **0**으로 설정된 경우에는 설정이 변경되지 않으며 Oracle 게시자 구성이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-218">If the entry exists, but is set to **0**, the setting will not be changed; the configuration of the Oracle Publisher will fail.</span></span>  
  
 <span data-ttu-id="a24c5-219">레지스트리 설정을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="a24c5-219">To view and modify the registry setting:</span></span>  
  
1.  <span data-ttu-id="a24c5-220">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-220">Click **Start**, and then click **Run**.</span></span>  
  
2.  <span data-ttu-id="a24c5-221">**실행** 대화 상자에 **regedit**를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-221">In the **Run** dialog box, type **regedit**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="a24c5-222">Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\ *\<InstanceName>* \Providers.</span><span class="sxs-lookup"><span data-stu-id="a24c5-222">Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\*\<InstanceName>* \Providers.</span></span>  
  
     <span data-ttu-id="a24c5-223">Providers 아래에는 OraOLEDB.Oracle 폴더가 있어야 하며</span><span class="sxs-lookup"><span data-stu-id="a24c5-223">Included under Providers should be a folder named OraOLEDB.Oracle.</span></span> <span data-ttu-id="a24c5-224">이 폴더 내에 이름이 **AllowInProcess**이고 값이 **1**인 DWORD 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-224">Within this folder should be the DWORD value name **AllowInProcess**, with a value of **1**.</span></span>  
  
4.  <span data-ttu-id="a24c5-225">**AllowInProcess** 가 **0**으로 설정되어 있으면 레지스트리 항목을 **1**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-225">If you determine that **AllowInProcess** is set to **0**, update the registry entry to **1**:</span></span>  
  
    1.  <span data-ttu-id="a24c5-226">항목을 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-226">Right-click the entry, and then click **Modify**.</span></span>  
  
    2.  <span data-ttu-id="a24c5-227">**문자열 편집** 대화 상자의 **값 데이터** 필드에 **1** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-227">In the **Edit String** dialog box, type **1** in the **Value data** field.</span></span>  
  
## <a name="sql-server-error-21684-is-raised"></a><span data-ttu-id="a24c5-228">SQL Server 오류 21684가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-228">SQL Server Error 21684 Is Raised</span></span>  
 <span data-ttu-id="a24c5-229">관리 사용자 계정에 충분한 권한이 없으면 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-229">If the administrative user account does not have sufficient privileges, the following error message is shown:</span></span>  
  
 <span data-ttu-id="a24c5-230">“Oracle 게시자 '%s'의 관리자 로그인과 연관된 사용 권한이 충분하지 않습니다.”</span><span class="sxs-lookup"><span data-stu-id="a24c5-230">"The permissions associated with the administrator login for Oracle publisher '%s' are not sufficient."</span></span>  
  
 <span data-ttu-id="a24c5-231">사용자에게 부여된 사용 권한을 확인하려면 `SELECT * from session_privs`쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-231">To verify the permissions granted to the user, execute the following query: `SELECT * from session_privs`.</span></span> <span data-ttu-id="a24c5-232">출력은 다음과 같은 형태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-232">The output should be similar to the following:</span></span>  
  
 `PRIVILEGE`  
  
 `------------------`  
  
 `CREATE SESSION`  
  
 `CREATE TABLE`  
  
 `CREATE PUBLIC SYNONYM`  
  
 `DROP PUBLIC SYNONYM`  
  
 `CREATE VIEW`  
  
 `CREATE SEQUENCE`  
  
 `CREATE PROCEDURE`  
  
 `CREATE TRIGGER`  
  
## <a name="you-encounter-permissions-issues-for-the-replication-user-schema"></a><span data-ttu-id="a24c5-233">복제 사용자 스키마에 대한 사용 권한 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-233">You Encounter Permissions Issues for the Replication User Schema</span></span>  
 <span data-ttu-id="a24c5-234">복제 사용자 스키마에는 [Oracle 게시자 구성](configure-an-oracle-publisher.md)의 "수동으로 사용자 스키마 만들기"에 설명된 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-234">The replication user schema must have the permissions described in "Creating the User Schema Manually" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="oracle-error-ora-01000"></a><span data-ttu-id="a24c5-235">Oracle 오류 ORA-01000</span><span class="sxs-lookup"><span data-stu-id="a24c5-235">Oracle Error ORA-01000</span></span>  
 <span data-ttu-id="a24c5-236">복제는 게시에 아티클을 추가할 때 Oracle 게시자에 커서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-236">Replication uses cursors on the Oracle Publisher during the process of adding articles to a publication.</span></span> <span data-ttu-id="a24c5-237">이때 게시자에서 사용할 수 있는 최대 커서 수가 초과되어</span><span class="sxs-lookup"><span data-stu-id="a24c5-237">It is possible to exceed the maximum number of cursors available on the Publisher during this process.</span></span> <span data-ttu-id="a24c5-238">다음 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-238">If this occurs, the following error is raised:</span></span>  
  
 <span data-ttu-id="a24c5-239">"ORA-01000: maximum open cursors exceeded"</span><span class="sxs-lookup"><span data-stu-id="a24c5-239">"ORA-01000: maximum open cursors exceeded"</span></span>  
  
 <span data-ttu-id="a24c5-240">이 문제를 방지하려면 Oracle 데이터베이스에서 **max_open_cursors** 설정을 충분히 높은 수(최소 1000)로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-240">To avoid this problem, ensure that the **max_open_cursors** setting in the Oracle databases is set to a sufficiently high number (at least 1000).</span></span> <span data-ttu-id="a24c5-241">이 설정에 대한 자세한 내용은 Oracle 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-241">For more information about this setting, see the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-01555"></a><span data-ttu-id="a24c5-242">Oracle 오류 ORA-01555</span><span class="sxs-lookup"><span data-stu-id="a24c5-242">Oracle Error ORA-01555</span></span>  
 <span data-ttu-id="a24c5-243">다음 Oracle 데이터베이스 오류는 스냅샷 복제와는 관계가 없으며 Oracle에서 일관된 읽기를 수행할 수 있는 데이터 뷰를 생성하는 방식과 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-243">The following Oracle database error is not related to snapshot replication; it is related to how Oracle constructs read-consistent views of data:</span></span>  
  
 <span data-ttu-id="a24c5-244">"ORA-01555: Snapshot too old"</span><span class="sxs-lookup"><span data-stu-id="a24c5-244">"ORA-01555: Snapshot too old"</span></span>  
  
 <span data-ttu-id="a24c5-245">Oracle에서는 롤백 세그먼트라는 개체를 사용하여 SQL 문이 실행된 시점에서 일관된 읽기를 수행할 수 있는 데이터 뷰를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-245">Using objects known as rollback segments, Oracle constructs read-consistent views of data as of the point in time a SQL statement is issued.</span></span> <span data-ttu-id="a24c5-246">다른 동시 세션에서 롤백 정보를 덮어쓰는 경우 "snapshot too old" 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-246">A "snapshot too old" error might occur when rollback information is overwritten by other concurrent sessions.</span></span> <span data-ttu-id="a24c5-247">Oracle 9i 이전에서는 이 오류의 발생 빈도를 줄이기 위해 롤백 세그먼트의 크기 및/또는 수를 늘리고 큰 트랜잭션을 특정 롤백 세그먼트에 할당하는 방법이 권장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-247">Prior to Oracle 9i, the recommended method of reducing the frequency of this error was to increase the size and/or number of rollback segments, and to assign large transactions to a specific rollback segment.</span></span>  
  
 <span data-ttu-id="a24c5-248">Oracle 9i에서는 롤백 세그먼트를 대체하는 UNDO 테이블스페이스 개념을 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-248">In Oracle 9i, Oracle introduced the UNDO tablespace concept, which replaces the rollback segment.</span></span> <span data-ttu-id="a24c5-249">Oracle 9i에서 "snapshot too old" 오류를 방지하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-249">To prevent the "snapshot too old" error in Oracle 9i, it is recommended that you:</span></span>  
  
-   <span data-ttu-id="a24c5-250">사용 가능한 공간을 적절히 지정한 다음 UNDO 테이블스페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-250">Create an UNDO tablespace with an appropriate amount of free space.</span></span>  
  
-   <span data-ttu-id="a24c5-251">테이블스페이스에 보존이 보장되는 기간을 설정합니다(Oracle 10G 이상).</span><span class="sxs-lookup"><span data-stu-id="a24c5-251">Set the retention guarantee on the tablespace (Oracle 10G and greater).</span></span>  
  
-   <span data-ttu-id="a24c5-252">Oracle 초기화 매개 변수인 UNDO_MANAGEMENT 및 UNDO_RETENTION을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-252">Configure the Oracle initialization parameters UNDO_MANAGEMENT and UNDO_RETENTION.</span></span>  
  
 <span data-ttu-id="a24c5-253">"snapshot too old" 오류 방지 방법에 대한 자세한 내용은 Oracle 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a24c5-253">For further details about avoiding the "snapshot too old" error, consult the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-22285"></a><span data-ttu-id="a24c5-254">Oracle 오류 ORA-22285</span><span class="sxs-lookup"><span data-stu-id="a24c5-254">Oracle Error ORA-22285</span></span>  
 <span data-ttu-id="a24c5-255">테이블에 BFILE 열이 포함되어 있는 경우에는 이 열의 데이터가 파일 시스템에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-255">If a table includes a BFILE column, the data for the column is stored in the file system.</span></span> <span data-ttu-id="a24c5-256">다음 구문을 사용하여 복제 관리 사용자 계정에 데이터가 저장되어 있는 디렉터리에 대한 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-256">The replication administrative user account must be granted access to the directory in which the data is stored using the following syntax:</span></span>  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 <span data-ttu-id="a24c5-257">액세스 권한을 부여하지 않으면 로그 판독기 에이전트에서 다음 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-257">If access is not granted, the following error is raised by the Log Reader Agent:</span></span>  
  
 <span data-ttu-id="a24c5-258">"ORA-22285: non-existent directory or file for FILEOPEN operation"</span><span class="sxs-lookup"><span data-stu-id="a24c5-258">"ORA-22285: non-existent directory or file for FILEOPEN operation"</span></span>  
  
## <a name="changes-are-made-that-require-reconfiguration-of-the-publisher"></a><span data-ttu-id="a24c5-259">게시자를 다시 구성해야 하는 변경 내용이 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-259">Changes Are Made That Require Reconfiguration of the Publisher</span></span>  
 <span data-ttu-id="a24c5-260">복제 메타데이터 테이블 또는 프로시저를 변경하면 게시자를 삭제하고 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-260">Changes to replication metadata tables or procedures require that you drop and reconfigure the Publisher.</span></span> <span data-ttu-id="a24c5-261">게시자를 다시 구성하려면 게시자를 삭제하고 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL 또는 RMO를 사용하여 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-261">To reconfigure the Publisher, you must drop the Publisher and configure it again using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL, or RMO.</span></span> <span data-ttu-id="a24c5-262">게시자 구성에 대한 자세한 내용은 [Oracle 게시자 구성](configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-262">For information about configuring the Publisher, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="a24c5-263">**Oracle 게시자를 삭제하려면(** SQL Server Management Studio **)**</span><span class="sxs-lookup"><span data-stu-id="a24c5-263">**To drop an Oracle Publisher (** SQL Server Management Studio **)**</span></span>  
  
1.  <span data-ttu-id="a24c5-264">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 에서 Oracle 게시자에 대한 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-264">Connect to the Distributor for the Oracle Publisher in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and expand the server node.</span></span>  
  
2.  <span data-ttu-id="a24c5-265">**복제**를 마우스 오른쪽 단추로 클릭한 다음 **배포자 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-265">Right-click **Replication**, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="a24c5-266">**배포자 속성** 대화 상자의 **게시자** 페이지에서 Oracle 게시자에 대한 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-266">On the **Publishers** page of the **Distributor Properties** dialog box, clear the check box for the Oracle Publisher.</span></span>  
  
4.  <span data-ttu-id="a24c5-267">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-267">Click **OK**.</span></span>  
  
 <span data-ttu-id="a24c5-268">**Transact-SQL을 사용하여 Oracle 게시자를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="a24c5-268">**To drop an Oracle Publisher (Transact-SQL)**</span></span>  
  
-   <span data-ttu-id="a24c5-269">**sp_dropdistpublisher**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a24c5-269">Execute **sp_dropdistpublisher**.</span></span> <span data-ttu-id="a24c5-270">자세한 내용은 [sp_dropdistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24c5-270">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24c5-271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a24c5-271">See Also</span></span>  
 <span data-ttu-id="a24c5-272">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="a24c5-272">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="a24c5-273">Oracle 게시 개요</span><span class="sxs-lookup"><span data-stu-id="a24c5-273">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
