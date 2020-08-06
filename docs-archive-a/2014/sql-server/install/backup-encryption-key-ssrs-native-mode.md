---
title: 백업 암호화 키 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d82a9b594e4a7ef7ceeb6737932e7e42a7f6fb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650524"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a><span data-ttu-id="78611-102">백업 암호화 키(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="78611-102">Backup Encryption Key (SSRS Native Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="78611-103">는 암호화 키를 사용하여 보고서 서버 데이터베이스에 저장된 중요한 데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-103">uses an encryption key to secure sensitive data that is stored in the report server database.</span></span> <span data-ttu-id="78611-104">암호화된 연결 문자열 및 자격 증명에 계속 액세스하려 이 키를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-104">Having a backup of this key is essential for ensuring continued access to encrypted connection strings and credentials.</span></span> <span data-ttu-id="78611-105">보고서 서버 데이터베이스를 다른 컴퓨터로 이동하거나 보고서 서버 서비스 계정의 사용자 이름 또는 암호를 변경할 경우 이 키의 복사본을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-105">You must have a backup copy of this key if you move the report server database to another computer or if you change the user name or password of the Report Server service account.</span></span> <span data-ttu-id="78611-106">두 작업을 수행하려면 이전에 만든 백업 복사본에서 키를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-106">Both operations require that you restore the key from a backup copy that you previously created.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="78611-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="78611-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="78611-108">암호화 키 백업 대화 상자를 열려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자의 탐색 창에서 **암호화 키**를 클릭한 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-108">To open the Backup Encryption Key dialog box, click **Encryption Keys** in the navigation pane of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, and then click **Backup**.</span></span> <span data-ttu-id="78611-109">이 대화 상자는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자의 서비스 계정 페이지를 사용하여 서비스 계정을 업데이트할 때도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78611-109">This dialog box also appears when you update the service account using the Service Account page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="78611-110">Configuration Manager에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78611-110">For more information on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="78611-111">옵션</span><span class="sxs-lookup"><span data-stu-id="78611-111">Options</span></span>  
 <span data-ttu-id="78611-112">**파일 위치**</span><span class="sxs-lookup"><span data-stu-id="78611-112">**File Location**</span></span>  
 <span data-ttu-id="78611-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 의 파일 이름과 위치를 대칭 키에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-113">Specify a file name and location for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to the symmetric key.</span></span> <span data-ttu-id="78611-114">대칭 키는 일반 텍스트로 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78611-114">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="78611-115">해당 파일을 보호하려면 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-115">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="78611-116">**암호**</span><span class="sxs-lookup"><span data-stu-id="78611-116">**Password**</span></span>  
 <span data-ttu-id="78611-117">무단 액세스로부터 파일을 보호하는 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-117">Type a password that protects the file against unauthorized access.</span></span> <span data-ttu-id="78611-118">암호를 아는 사용자만 파일 내에서 잠긴 키를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78611-118">Only users who know the password will be able to restore the key that is locked inside the file.</span></span> <span data-ttu-id="78611-119">이처럼 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]는 강력한 암호 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-119">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enforces a strong password policy.</span></span> <span data-ttu-id="78611-120">암호는 8자 이상이어야 하며 대/소문자 조합과 하나 이상의 기호를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-120">The password must be at least 8 characters and include a combination of uppercase and lowercase alphanumeric characters and at least one symbol character.</span></span>  
  
 <span data-ttu-id="78611-121">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="78611-121">**Confirm Password**</span></span>  
 <span data-ttu-id="78611-122">입력한 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78611-122">Re-type the password you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78611-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78611-123">See Also</span></span>  
 <span data-ttu-id="78611-124">[Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="78611-124">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="78611-125">[Reporting Services 암호화 키 백업 및 복원](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="78611-125">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="78611-126">[암호화 키 삭제 및 다시 만들기&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="78611-126">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="78611-127">[보고서 서버 초기화&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="78611-127">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 <span data-ttu-id="78611-128">[암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="78611-128">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="78611-129">SSRS 기본 모드 &#40;암호화 키&#41;</span><span class="sxs-lookup"><span data-stu-id="78611-129">Encryption Keys &#40;SSRS Native Mode&#41;</span></span>](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
