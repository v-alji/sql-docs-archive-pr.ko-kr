---
title: rskeymgmt 유틸리티(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], encryption
- joining report server instances [SQL Server]
- report server scale-out deployments [Reporting Services]
- cryptography [Reporting Services]
- multiple report server instances
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], scale-out deployments
- encryption [Reporting Services]
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 53f1318d-bd2d-4c08-b19f-c8b698b5b3d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae4bdd6656cf5b29f8fd40fcf730f49a6de8f32e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735988"
---
# <a name="rskeymgmt-utility-ssrs"></a><span data-ttu-id="aed74-102">rskeymgmt 유틸리티(SSRS)</span><span class="sxs-lookup"><span data-stu-id="aed74-102">rskeymgmt Utility (SSRS)</span></span>
  <span data-ttu-id="aed74-103">중요한 보고서 서버 데이터를 무단 액세스로부터 보호하는 데 사용할 대칭 키를 추출, 복원, 생성 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-103">Extracts, restores, creates, and deletes the symmetric key used to protect sensitive report server data against unauthorized access.</span></span> <span data-ttu-id="aed74-104">이 유틸리티를 사용하여 수평적 스케일 아웃 배포에서 보고서 서버 인스턴스를 결합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-104">This utility is also used to join report server instances in a scale-out deployment.</span></span> <span data-ttu-id="aed74-105">*보고서 서버 수평적 스케일 아웃 배포* 란 하나의 보고서 서버 데이터베이스를 공유하는 여러 보고서 서버 인스턴스를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-105">A *report server scale-out deployment* refers to multiple report server instances that share a single report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed74-106">구문</span><span class="sxs-lookup"><span data-stu-id="aed74-106">Syntax</span></span>  
  
```  
  
      rskeymgmt {-?}  
{-eextract}  
{-aapply}  
{-ddeleteall}  
{-srecreatekey}  
{-rremoveinstancekey}  
{-jjoinfarm}  
{-iinstance}  
{-ffile}  
{-pencryptionpassword}  
{-mremotecomputer}  
{-ninstancenameofremotecomputer}  
{-uadministratoruseraccount}  
{-vadministratorpassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="aed74-107">인수</span><span class="sxs-lookup"><span data-stu-id="aed74-107">Arguments</span></span>  
 <span data-ttu-id="aed74-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="aed74-108">**-?**</span></span>  
 <span data-ttu-id="aed74-109">**rskeymgmt** 인수의 구문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-109">Displays the syntax of **rskeymgmt** arguments.</span></span>  
  
 <span data-ttu-id="aed74-110">**-e**</span><span class="sxs-lookup"><span data-stu-id="aed74-110">**-e**</span></span>  
 <span data-ttu-id="aed74-111">파일로 복사할 수 있도록 보고서 서버 인스턴스의 데이터를 암호화 및 해독하는 데 사용할 대칭 키를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-111">Extracts the symmetric key used to encrypt and decrypt data for the report server instance so that you can copy it to a file.</span></span>  
  
 <span data-ttu-id="aed74-112">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-112">This argument does not take a value.</span></span> <span data-ttu-id="aed74-113">그러나 압축 풀기를 완료하려면 명령줄에 추가 인수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-113">However, you must include additional arguments on the command line to complete the extraction.</span></span> <span data-ttu-id="aed74-114">지정해야 할 인수에는 `-f` 및 `-p` 인수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-114">The arguments that you must specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="aed74-115">**-a**</span><span class="sxs-lookup"><span data-stu-id="aed74-115">**-a**</span></span>  
 <span data-ttu-id="aed74-116">기존 대칭 키를 암호로 보호된 백업 파일에 제공한 복사본으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-116">Replaces an existing symmetric key with a copy that you provide in a password protected backup file.</span></span> <span data-ttu-id="aed74-117">대칭 키의 모든 인스턴스가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-117">All instances of the symmetric key are updated.</span></span>  
  
 <span data-ttu-id="aed74-118">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-118">This argument does not take a value.</span></span> <span data-ttu-id="aed74-119">그러나 적용된 키가 포함된 파일을 선택하려면 명령줄에 추가 인수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-119">However, you must include additional arguments on the command line to select the file that contains the key to be applied.</span></span> <span data-ttu-id="aed74-120">지정할 수 있는 인수에는 `-f` 및 `-p` 인수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-120">The arguments that you can specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="aed74-121">**-d**</span><span class="sxs-lookup"><span data-stu-id="aed74-121">**-d**</span></span>  
 <span data-ttu-id="aed74-122">모든 대칭 키 인스턴스를 삭제하고 보고서 서버 데이터베이스에서 암호화된 모든 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-122">Deletes all symmetric key instances and all encrypted data in a report server database.</span></span> <span data-ttu-id="aed74-123">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-123">This argument does not take a value.</span></span>  
  
 `-s`  
 <span data-ttu-id="aed74-124">새 대칭 키를 생성하고 이 키를 사용하여 암호화된 모든 내용을 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-124">Generates a new symmetric key and re-encrypts all encrypted content using the new key.</span></span> <span data-ttu-id="aed74-125">대칭 키의 모든 인스턴스가 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-125">All instances of the symmetric key are regenerated.</span></span>  
  
 `-j`  
 <span data-ttu-id="aed74-126">로컬 보고서 서버 인스턴스에서 사용하는 보고서 서버 데이터베이스를 공유하도록 원격 보고서 서버 인스턴스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-126">Configures a remote report server instance to share the report server database that is used by the local report server instance.</span></span>  
  
 <span data-ttu-id="aed74-127">**-r**  *installationID*</span><span class="sxs-lookup"><span data-stu-id="aed74-127">**-r**  *installationID*</span></span>  
 <span data-ttu-id="aed74-128">특정 보고서 서버 인스턴스에 대한 대칭 키 정보를 제거합니다. 이에 따라 수평적 스케일 아웃 배포에서 보고서 서버도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-128">Removes the symmetric key information for a specific report server instance, thereby removing the report server from a scale-out deployment.</span></span> <span data-ttu-id="aed74-129">*installationID* 는 RSReportserver.config 파일에 포함된 GUID 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-129">The *installationID* is a GUID value that can be found in the RSReportserver.config file.</span></span>  
  
 <span data-ttu-id="aed74-130">`-f`  *file*</span><span class="sxs-lookup"><span data-stu-id="aed74-130">`-f`  *file*</span></span>  
 <span data-ttu-id="aed74-131">대칭 키의 백업 복사본을 저장하는 파일의 정규화된 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-131">Specifies a fully qualified path to the file that stores a backup copy of the symmetric keys.</span></span>  
  
 <span data-ttu-id="aed74-132">**rskeymgmt -e**의 경우 대칭 키가 지정한 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-132">For **rskeymgmt -e**, the symmetric key is written to the file you specify.</span></span>  
  
 <span data-ttu-id="aed74-133">**rskeymgmt -a**의 경우 파일에 저장된 대칭 키 값이 보고서 서버 인스턴스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-133">For **rskeymgmt -a**, the symmetric key value stored in the file is applied to the report server instance.</span></span>  
  
 <span data-ttu-id="aed74-134">`-p`  *암호*</span><span class="sxs-lookup"><span data-stu-id="aed74-134">`-p`  *password*</span></span>  
 <span data-ttu-id="aed74-135">`-f`의 경우 필수 인수입니다. 대칭 키를 백업하거나 적용하는 데 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-135">(Required for `-f`) Specifies the password used to back up or apply a symmetric key.</span></span> <span data-ttu-id="aed74-136">이 값은 비워 둘 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-136">This value cannot be empty.</span></span>  
  
 `-i`  
 <span data-ttu-id="aed74-137">로컬 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-137">Specifies a local report server instance.</span></span> <span data-ttu-id="aed74-138">기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 보고서 서버를 설치한 경우 이 인수는 옵션입니다. `-i`의 기본값은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-138">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-i` is MSSQLSERVER).</span></span> <span data-ttu-id="aed74-139">보고서 서버를 명명된 인스턴스로 설치한 경우 `-i`이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-139">If you installed the report server as a named instance, `-i` is required.</span></span>  
  
 `-m`  
 <span data-ttu-id="aed74-140">보고서 서버 수평적 스케일 아웃 배포에 결합하는 보고서 서버 인스턴스를 호스팅하는 원격 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-140">Specifies the name of the remote computer that hosts the report server instance you are joining to the report server scale-out deployment.</span></span> <span data-ttu-id="aed74-141">네트워크에서 식별할 수 있는 컴퓨터 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-141">Use the name of the computer that identifies it on your network.</span></span>  
  
 `-n`  
 <span data-ttu-id="aed74-142">원격 컴퓨터의 보고서 서버 인스턴스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-142">Specifies the name of the report server instance on a remote computer.</span></span> <span data-ttu-id="aed74-143">기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 보고서 서버를 설치한 경우 이 인수는 옵션입니다. `-n`의 기본값은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-143">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-n` is MSSQLSERVER).</span></span> <span data-ttu-id="aed74-144">보고서 서버를 명명된 인스턴스로 설치한 경우 `-n`이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-144">If you installed the report server as a named instance, `-n` is required.</span></span>  
  
 <span data-ttu-id="aed74-145">`-u`  *useraccount*</span><span class="sxs-lookup"><span data-stu-id="aed74-145">`-u`  *useraccount*</span></span>  
 <span data-ttu-id="aed74-146">수평적 스케일 아웃 배포에 결합하는 원격 컴퓨터의 관리자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-146">Specifies the administrator account on the remote computer that you are joining to the scale-out deployment.</span></span> <span data-ttu-id="aed74-147">계정을 지정하지 않으면 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-147">If an account is not specified, the credentials of the current user are used.</span></span>  
  
 <span data-ttu-id="aed74-148">`-v`  *암호*</span><span class="sxs-lookup"><span data-stu-id="aed74-148">`-v`  *password*</span></span>  
 <span data-ttu-id="aed74-149">`-u`의 경우 필수 인수입니다. 수평적 스케일 아웃 배포에 결합할 원격 컴퓨터의 관리자 계정 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-149">(Required for `-u`) Specifies the password of an administrator account on the remote computer that you want to join to the scale-out deployment.</span></span>  
  
 <span data-ttu-id="aed74-150">**-t**  *추적*</span><span class="sxs-lookup"><span data-stu-id="aed74-150">**-t**  *trace*</span></span>  
 <span data-ttu-id="aed74-151">추적 로그에 오류 메시지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-151">Outputs error messages to the trace log.</span></span> <span data-ttu-id="aed74-152">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-152">This argument does not take a value.</span></span> <span data-ttu-id="aed74-153">자세한 내용은 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aed74-153">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="aed74-154">사용 권한</span><span class="sxs-lookup"><span data-stu-id="aed74-154">Permissions</span></span>  
 <span data-ttu-id="aed74-155">이 도구를 실행하려면 로컬 관리자 권한이 있어야 하며 보고서 서버를 호스팅하는 컴퓨터에서 로컬로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-155">You must be a local administrator to run the tool, and you must run it locally on the computer that hosts the report server.</span></span> <span data-ttu-id="aed74-156">rskeymgmt 유틸리티는 로컬 보고서 서버 Windows 인스턴스에 사용할 수 있습니다. 이 유틸리티는 보고서 서버 Windows 서비스의 원격 인스턴스에 연결할 수 없으므로 원격 보고서 서버 인스턴스의 암호화 키를 관리하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-156">The rskeymgmt utility works with the local Report Server Windows instance (the utility cannot connect to remote instances of the Report Server Windows service so it cannot be used to manage the encryption keys of a remote report server instance).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aed74-157">`-u` 및 `-v` 인수를 사용하는 경우 원격 컴퓨터에 대해 관리자 권한이 있는 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-157">If you are using the `-u` and `-v` arguments, be sure to specify an account that has administrator permissions on the remote computer.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aed74-158">예</span><span class="sxs-lookup"><span data-stu-id="aed74-158">Examples</span></span>  
 <span data-ttu-id="aed74-159">다음 예에서는 **rskeymgmt**를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-159">The following examples illustrate ways of using **rskeymgmt**.</span></span> <span data-ttu-id="aed74-160">다음 예에서는 암호화 키를 추출, 복원 및 삭제하는 방법과 보고서 서버 수평적 스케일 아웃 배포를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-160">The following examples show how to extract, restore, and delete encryption keys, and how to configure a report server scale-out deployment.</span></span>  
  
#### <a name="extracting-encryption-keys"></a><span data-ttu-id="aed74-161">암호화 키 추출</span><span class="sxs-lookup"><span data-stu-id="aed74-161">Extracting Encryption Keys</span></span>  
 <span data-ttu-id="aed74-162">이 예에서는 암호화 키의 백업 복사본을 만들고 플로피 디스크의 암호로 보호된 파일에 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-162">This example shows how to create a backup copy of the encryption key and save it to a password-protected file on a floppy disk.</span></span> <span data-ttu-id="aed74-163">보고서 서버를 명명된 인스턴스로 설치한 경우 `-i` 인수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-163">If the report server is installed as a named instance, add the `-i` argument.</span></span>  
  
```  
rskeymgmt -e -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="restoring-encryption-keys"></a><span data-ttu-id="aed74-164">암호화 키 복원</span><span class="sxs-lookup"><span data-stu-id="aed74-164">Restoring Encryption Keys</span></span>  
 <span data-ttu-id="aed74-165">이 예에서는 암호화 키를 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-165">This example shows how to replace the encryption key.</span></span> <span data-ttu-id="aed74-166">암호화 키의 백업 복사본 위치와 이 파일의 잠금을 해제하는 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-166">You must specify the location of the backup copy of the key and the password that unlocks the file.</span></span>  
  
```  
rskeymgmt -a -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="deleting-encryption-keys-and-encrypted-content"></a><span data-ttu-id="aed74-167">암호화 키 및 암호화된 내용 삭제</span><span class="sxs-lookup"><span data-stu-id="aed74-167">Deleting Encryption Keys and Encrypted Content</span></span>  
 <span data-ttu-id="aed74-168">이 예에서는 보고서 서버에 저장된 모든 암호화 키를 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-168">This example shows how to delete all encryption keys stored in a report server.</span></span> <span data-ttu-id="aed74-169">보고서 서버 수평적 스케일 아웃 배포로 설치한 경우 이 배포에 포함된 모든 보고서 서버 인스턴스의 암호화 키가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-169">If your installation is a report server scale-out deployment, the encryption keys for all report server instances that are included in the deployment will be deleted.</span></span> <span data-ttu-id="aed74-170">암호화 키를 삭제하면 보고서 서버 데이터베이스에서 암호화된 기존 값도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-170">Deleting an encryption key also deletes any existing encrypted values in the report server database.</span></span> <span data-ttu-id="aed74-171">암호화된 내용에 대한 자세한 내용은 [암호화된 보고서 서버 데이터 저장&#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aed74-171">For more information about encrypted content, see [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md).</span></span>  
  
```  
rskeymgmt -d  
```  
  
#### <a name="joining-a-remote-report-server-named-instance-to-a-scale-out-deployment"></a><span data-ttu-id="aed74-172">원격 보고서 서버의 명명된 인스턴스를 수평적 확장 배포에 결합</span><span class="sxs-lookup"><span data-stu-id="aed74-172">Joining a Remote Report Server Named Instance to a Scale-out Deployment</span></span>  
 <span data-ttu-id="aed74-173">이 예에서는 원격 컴퓨터에 설치된 보고서 서버 인스턴스를 보고서 서버 수평적 스케일 아웃 배포에 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-173">This example shows how to add a report server instance that is installed on a remote computer to a report server scale-out deployment.</span></span> <span data-ttu-id="aed74-174">공유되는 데이터베이스를 사용하도록 이미 구성된 컴퓨터 중 하나에서 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-174">You must run the command on one of the computers that is already configured to use the shared database.</span></span> <span data-ttu-id="aed74-175">명령 인수는 수평적 스케일 아웃 배포에 포함할 원격 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-175">The command arguments specify the remote report server instance you want to join to the scale-out deployment.</span></span>  
  
```  
rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="aed74-176">보고서 서버 수평적 스케일 아웃 배포란 여러 보고서 서버 인스턴스가 같은 보고서 서버 데이터베이스를 공유하는 배포 모델을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-176">A report server scale-out deployment refers to a deployment model where multiple report server instances share the same report server database.</span></span> <span data-ttu-id="aed74-177">보고서 서버 데이터베이스에 대칭 키를 저장하는 모든 보고서 서버 인스턴스에서 이 데이터베이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-177">A report server database can be used by any report server instance that stores its symmetric keys in the database.</span></span> <span data-ttu-id="aed74-178">예를 들어 보고서 서버 데이터베이스에 3개의 보고서 서버 인스턴스에 대한 키 정보가 포함된 경우 세 인스턴스는 모두 같은 수평적 스케일 아웃 배포의 멤버로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-178">For example, if a report server database contains key information for three report server instances, all three instances are considered to members of the same scale-out deployment.</span></span>  
  
#### <a name="joining-report-server-instances-on-the-same-computer"></a><span data-ttu-id="aed74-179">같은 컴퓨터에서 보고서 서버 인스턴스 조인</span><span class="sxs-lookup"><span data-stu-id="aed74-179">Joining Report Server Instances on the Same Computer</span></span>  
 <span data-ttu-id="aed74-180">같은 컴퓨터에 설치된 여러 보고서 서버 인스턴스에서 스케일 아웃 배포를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-180">You can create a scale-out deployment from multiple report server instances that are installed on the same computer.</span></span> <span data-ttu-id="aed74-181">로컬로 설치된 보고서 서버 인스턴스를 조인하는 경우에는 `-u` 및 `-v` 인수를 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="aed74-181">Do not set the `-u` and `-v` arguments if you are joining report server instances that are installed locally.</span></span> <span data-ttu-id="aed74-182">`-u` 및 `-v` 인수는 원격 컴퓨터에서 인스턴스를 조인하는 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-182">The `-u` and `-v` arguments are used only when you are joining an instance from a remote computer.</span></span> <span data-ttu-id="aed74-183">로컬인 경우 이러한 인수를 지정하면 "로컬 연결에 대해 사용자 자격 증명을 사용할 수 없습니다" 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-183">If you specify the arguments, you will get the following error: "User credentials cannot be used for local connections."</span></span>  
  
 <span data-ttu-id="aed74-184">다음 예에서는 여러 로컬 인스턴스를 사용하여 스케일 아웃 배포를 만드는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-184">The following example illustrates the syntax for creating a scale-out deployment using multiple local instances.</span></span> <span data-ttu-id="aed74-185">이 예에서 <>는 `initializedinstance` 보고서 서버 데이터베이스를 사용 하도록 이미 초기화 된 인스턴스의 이름이 고, `newinstance`> <은 배포에 추가 하려는 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-185">In this example, <`initializedinstance`> is the name of an instance that is already initialized to use the report server database, and <`newinstance`> is the name of the instance that you want to add to the deployment:</span></span>  
  
```  
rskeymgmt -j -i <initializedinstance> -m <computer name> -n <newinstance>  
```  
  
#### <a name="removing-encryption-keys-for-a-single-report-server-in-a-scale-out-deployment"></a><span data-ttu-id="aed74-186">수평적 확장 배포에서 단일 보고서 서버의 암호화 키 제거</span><span class="sxs-lookup"><span data-stu-id="aed74-186">Removing Encryption Keys for a Single Report Server in a Scale-out Deployment</span></span>  
 <span data-ttu-id="aed74-187">이 예에서는 보고서 서버 수평적 스케일 아웃 배포에서 단일 보고서 서버의 암호화 키를 제거하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-187">This example shows how to remove the encryption keys for a single report server in a report server scale-out deployment.</span></span> <span data-ttu-id="aed74-188">이 키는 보고서 서버 데이터베이스에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-188">The keys are removed from the report server database.</span></span> <span data-ttu-id="aed74-189">보고서 서버 인스턴스의 키가 제거되면 이 보고서 서버 인스턴스에서 데이터베이스의 암호화된 데이터에 더 이상 액세스할 수 없으며 수평적 스케일 아웃 배포에서 효과적으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-189">Once the keys for that report server instance are removed, that report server instance can no longer access encrypted data in the database, effectively removing it from the scale-out deployment.</span></span>  
  
 <span data-ttu-id="aed74-190">스케일 아웃 배포에서 보고서 서버 인스턴스를 제거하려면 설치 ID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-190">Removing a report server instance from a scale-out deployment requires you to specify an installation ID.</span></span> <span data-ttu-id="aed74-191">설치 ID는 암호화 키를 제거하려는 보고서 서버 인스턴스의 RSReportserver.config 파일에 저장된 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-191">The installation ID is a GUID stored in the RSReportserver.config file of the report server instance for which you want to remove encryption keys.</span></span> <span data-ttu-id="aed74-192">수평적 스케일 아웃 배포에서 제거할 컴퓨터에서 다음 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-192">You must run the following command on the computer that you want to remove from the scale-out deployment.</span></span> <span data-ttu-id="aed74-193">보고서 서버를 명명된 인스턴스로 설치한 경우 `-i` 인수를 사용하여 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-193">If the report server is installed as a named instance, use the `-i` argument to specify the instance.</span></span> <span data-ttu-id="aed74-194">자세한 내용은 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aed74-194">For more information, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
```  
rskeymgmt -r <installationID>  
```  
  
## <a name="file-location"></a><span data-ttu-id="aed74-195">파일 위치</span><span class="sxs-lookup"><span data-stu-id="aed74-195">File Location</span></span>  
 <span data-ttu-id="aed74-196">Rskeymgmt.exe는 \*\* \<*drive*> FileFiles\Microsoft sql Server\110\Tools\Binn\*\* 또는 at: filefiles \*\* \<*drive*> (x86) \Microsoft sql Server\110\Tools\Binn\*\*에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-196">Rskeymgmt.exe is located at **\<*drive*>:\Program Files\Microsoft SQL Server\110\Tools\Binn** or at **\<*drive*>:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="aed74-197">파일 시스템의 모든 폴더에서 유틸리티를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-197">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aed74-198">설명</span><span class="sxs-lookup"><span data-stu-id="aed74-198">Remarks</span></span>  
 <span data-ttu-id="aed74-199">보고서 서버는 저장된 자격 증명과 연결 정보를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-199">A report server encrypts stored credentials and connection information.</span></span> <span data-ttu-id="aed74-200">데이터를 암호화하는 데 공개 키와 대칭 키가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-200">A public key and a symmetric key are used to encrypt data.</span></span> <span data-ttu-id="aed74-201">보고서 서버를 실행하려면 보고서 서버 데이터베이스에 유효한 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-201">A report server database must have valid keys in order for the report server to run.</span></span> <span data-ttu-id="aed74-202">**rskeymgmt** 를 사용하여 키를 백업, 삭제 또는 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-202">You can use **rskeymgmt** to back up, delete, or restore the keys.</span></span> <span data-ttu-id="aed74-203">키를 복원할 수 없을 경우 이 도구는 더 이상 사용할 수 없는 암호화된 내용을 삭제하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-203">If the keys cannot be restored, this tool provides a way to delete encrypted content that can no longer be used.</span></span>  
  
 <span data-ttu-id="aed74-204">**rskeymgmt** 유틸리티를 사용하여 설치하는 동안 또는 초기화하는 동안 정의되는 키 집합을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-204">The **rskeymgmt** utility is used to manage the key set that is defined during Setup or during initialization.</span></span> <span data-ttu-id="aed74-205">이 유틸리티는 원격 프로시저 호출(RPC) 엔드포인트를 통해 로컬 보고서 서버 Windows 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-205">It connects to the local Report Server Windows service through a Remote Procedure Call (RPC) endpoint.</span></span> <span data-ttu-id="aed74-206">이 유틸리티가 올바르게 작동하려면 보고서 서버 Windows 서비스가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aed74-206">The Report Server Windows service must be running in order for this utility to work.</span></span>  
  
 <span data-ttu-id="aed74-207">암호화 키에 대한 자세한 내용은 [암호화 키 구성 및 관리&#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) 및 [보고서 서버 초기화&#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aed74-207">For more information about the encryption keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) and [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed74-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aed74-208">See Also</span></span>  
 <span data-ttu-id="aed74-209">[SSRS Configuration Manager 기본 모드 보고서 서버 스케일 아웃 배포 &#40;구성&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="aed74-209">[Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="aed74-210">[Reporting Services 보고서 서버&#40;기본 모드&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="aed74-210">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="aed74-211">[SSRS&#41;&#40;보고서 서버 명령 프롬프트 유틸리티](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aed74-211">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="aed74-212">암호화 키 구성 및 관리&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="aed74-212">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
