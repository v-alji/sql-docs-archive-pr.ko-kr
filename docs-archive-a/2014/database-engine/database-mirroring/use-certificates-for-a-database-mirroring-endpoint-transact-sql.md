---
title: 데이터베이스 미러링 엔드포인트에 인증서 사용(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c159e66e798524c41bf6e653283c299cc8393be5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649675"
---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a><span data-ttu-id="0081d-102">데이터베이스 미러링 엔드포인트에 대한 인증서 사용(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0081d-102">Use Certificates for a Database Mirroring Endpoint (Transact-SQL)</span></span>
  <span data-ttu-id="0081d-103">지정된 서버 인스턴스에서 데이터베이스 미러링에 인증서 인증을 사용하려면 시스템 관리자가 아웃바운드 및 인바운드 연결 모두에 인증서를 사용하도록 각 서버 인스턴스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-103">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="0081d-104">이 경우 아웃바운드 연결을 먼저 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-104">Outbound connections must be configured first.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0081d-105">서버 인스턴스의 모든 미러링 연결은 단일 데이터베이스 미러링 엔드포인트를 사용하며 이러한 엔드포인트를 만들 때는 서버 인스턴스의 인증 방법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span> <span data-ttu-id="0081d-106">따라서 데이터베이스 미러링에 사용할 서버 인스턴스마다 한 형식의 인증만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-106">Therefore, you can use only one form of authentication per server instance for database mirroring.</span></span>  
  
## <a name="configuring-outbound-connections"></a><span data-ttu-id="0081d-107">아웃바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="0081d-107">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="0081d-108">데이터베이스 미러링을 구성할 각 서버 인스턴스에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-108">Follow these steps on each server instance that you are configuring for database mirroring:</span></span>  
  
1.  <span data-ttu-id="0081d-109">**master** 데이터베이스에서 데이터베이스 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-109">In the **master** database, create a database master key.</span></span>  
  
2.  <span data-ttu-id="0081d-110">**master** 데이터베이스에서 서버 인스턴스의 암호화된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-110">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="0081d-111">서버 인스턴스의 인증서를 사용하여 해당 인스턴스의 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-111">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="0081d-112">인증서를 파일에 백업한 다음 안전한 다른 시스템으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-112">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="0081d-113">파트너와 미러링 모니터 각각에 대해 이러한 단계를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-113">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="0081d-114">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0081d-114">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
## <a name="configuring-inbound-connections"></a><span data-ttu-id="0081d-115">인바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="0081d-115">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="0081d-116">데이터베이스 미러링을 구성할 각 파트너에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-116">Next, follow these steps for each partner that you are configuring for database mirroring.</span></span> <span data-ttu-id="0081d-117">**master** 데이터베이스에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-117">In the **master** database:</span></span>  
  
1.  <span data-ttu-id="0081d-118">다른 시스템에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-118">Create a login for the other system.</span></span>  
  
2.  <span data-ttu-id="0081d-119">해당 로그인의 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-119">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="0081d-120">다른 서버 인스턴스의 미러링 엔드포인트에 대한 인증서를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-120">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="0081d-121">2단계에서 만든 사용자에 인증서를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-121">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="0081d-122">해당 미러링 엔드포인트에 대한 로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-122">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="0081d-123">미러링 모니터가 있는 경우 그에 대한 인바운드 연결도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-123">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="0081d-124">이렇게 하려면 양쪽 파트너 모두에서 미러링 모니터에 대한 로그인, 사용자 및 인증서를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-124">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="0081d-125">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0081d-125">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="0081d-126">보안</span><span class="sxs-lookup"><span data-stu-id="0081d-126">Security</span></span>  
 <span data-ttu-id="0081d-127">네트워크 보안을 보장할 수 없는 경우 데이터베이스 미러링 연결에 암호화를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-127">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span> <span data-ttu-id="0081d-128">자세한 내용은 [데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0081d-128">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
 <span data-ttu-id="0081d-129">인증서를 다른 시스템으로 복사할 때는 안전한 복사 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0081d-129">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="0081d-130">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0081d-130">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0081d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0081d-131">See Also</span></span>  
 <span data-ttu-id="0081d-132">[데이터베이스 마스터 키 만들기](../../relational-databases/security/encryption/create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="0081d-132">[Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="0081d-133">[CREATE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0081d-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="0081d-134">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="0081d-134">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="0081d-135">[SQL Server 데이터베이스 엔진 및 Azure SQL 데이터베이스에 대한 보안 센터](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span><span class="sxs-lookup"><span data-stu-id="0081d-135">[Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span></span>  
 [<span data-ttu-id="0081d-136">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0081d-136">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
